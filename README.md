# Django-with-ElasticSearch
当有新的 blog 被保存时触发一个 `signals`，在 ElasticSearch 中也生成一份并重建索引，最终在 Django 中实现高速查询 API: `search`

### 安装 ElasticSearch

```bash
mkdir elasticsearch-example
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.1.1.tar.gz
tar -xzf elasticsearch-5.1.1.tar.gz
./elasticsearch-5.1.1/bin/elasticsearch
```

### 安装运行 Django 项目

```bash
git clone https://github.com/tmpbook/Django-with-ElasticSearch.git
cd Django-with-ElasticSearch/elasticsearchproject

# 安装所需要的包
pip3 install -r requirements.txt

python manage.py runserver
# Starting development server at http://127.0.0.1:8000/

# 然后访问在这个 endpoint 添加一个 blog 对象
open http://127.0.0.1:8000/admin/elasticsearchapp/blogpost/add/

```

### 查看 ElasticSearch 并验证

```bash
curl -XGET 'localhost:9200/blogpost-index/blog_post_index/1?pretty'

# 应该是这样
{
  "_index" : "blogpost-index",
  "_type" : "blog_post_index",
  "_id" : "1",
  "_version" : 2,
  "found" : true,
  "_source" : {
    "author" : "admin",
    "posted_date" : "2017-12-21",
    "text" : "Blog content.",
    "title" : "blog title"
  }
}
```

### About me

知乎：[临书](https://www.zhihu.com/people/tmpbook/activities)

微信（WeChat）：

<div align=center>
    <img width="150" height="150" src="Wechat.jpeg"/>
</div>

<div align=right>谢谢阅读</div>
<div align=right>Thanks for watching</div>
