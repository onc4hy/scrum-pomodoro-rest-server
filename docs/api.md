* 敏捷番茄钟服务API接口文档

* 版本 0.1
* 作者 onc4hy@126.com

[TOC]

# 修改记录

# 接口规范
 * 当前接口版本为1.0
 * 接口协议采用 REST风格
 * 基本上数据HTTP请求方式参考常规REST方式，但简化为
	* 读取为GET
	* 写入除了标准REST风格，也统一支持POST提交，这是为了最大兼容性考虑
 * 数据支持格式目前为json格式
 * 接口URL地址前缀统一为 http://xxx.xxx.xxx/api/1 或 http://api.xxx.xxx/1
 * 接口URL地址格式为 http://xxx.xxx.xxx/api/1/tasks/show
 * 接口版本升级后同理在API前转换为版本号如 /api/2/tasks/show

# 用户管理
## 登录
 * login
    * 说明 使用用户邮箱/口令登录
    * URL格式 http://xxx.xxx.xxx/api/1/login
    * 支持格式 JSON
    * HTTP请求方式 POST
    * 请求参数
    	* email 参数名称:用户邮箱  是否必选:true 说明:
    	* password 参数名称:用户口令  是否必选:true 说明:
    * 返回结果
    	* 用户信息

## 注册
 * register
    * 说明 注册用户相关信息
    * URL格式 http://xxx.xxx.xxx/api/1/register
    * 支持格式 JSON
    * HTTP请求方式 POST
    * 请求参数
    	* email 参数名称:用户邮箱  是否必选:true 说明:
    	* password 参数名称:用户口令  是否必选:true 说明:
    * 返回结果
    	* 用户信息

## 登出
 * logout
    * 说明 用户退出登录
    * URL格式 http://xxx.xxx.xxx/api/1/logout
    * 支持格式 JSON
    * HTTP请求方式 GET
    * 请求参数
    	* email 参数名称:用户邮箱  是否必选:true 说明:
    	* password 参数名称:用户口令  是否必选:true 说明:
    * 返回结果
    	* 用户信息

## 获取用户信息
 * users/show
    * 说明 获取用户信息
    * URL格式 http://xxx.xxx.xxx/api/1/users/show
    * 支持格式 JSON
    * HTTP请求方式 GET
    * 请求参数
    	* source 参数名称:访问来源  是否必选:false 说明:
    	* token 参数名称:访问令牌 是否必选:false 说明:
    	* id 参数名称:用户ID 是否必选:true 说明:
    * 返回结果
    	* 用户信息

## 更新用户信息
 * users/update
    * 说明 获取用户信息
    * URL格式 http://xxx.xxx.xxx/api/1/users/update
    * 支持格式 JSON
    * HTTP请求方式 POST,PUT
    * 请求参数
    	* source 参数名称:访问来源  是否必选:false 说明:
    	* token 参数名称:访问令牌 是否必选:false 说明:
    	* id 参数名称:用户ID 是否必选:true 说明:
    * 返回结果
    	* 用户信息
	
# 数据管理
## 项目
 * 读取接口
	* projects/show
    	* 说明 根据项目ID获取项目信息
		* URL格式 http://xxx.xxx.xxx/api/1/projects/show
		* 支持格式 JSON			
		* HTTP请求方式 GET
		* 登录限制 是
		* 请求参数
			* source 参数名称:访问来源  是否必选:false 说明:
			* token 参数名称:访问令牌 是否必选:false 说明:
			* id 参数名称:项目ID 是否必选:true 说明:
		* 返回结果
 * 写入接口
    * projects/create
		* HTTP请求方式 POST
	* projects/update
		* HTTP请求方式 POST,PUT
	* projects/destroy
		* HTTP请求方式 POST,DELETE
 * 数据统计接口
	* projects/stats
		* HTTP请求方式 GET

## 迭代
 * 读取接口
	* iterators/show
		* HTTP请求方式 GET
 * 写入接口
	* iterators/create
		* HTTP请求方式 POST
	* iterators/destroy
		* HTTP请求方式 POST,DELETE
	* iterators/update
		* HTTP请求方式 POST,PUT
 * 数据统计接口
	* iterators/stats
		* HTTP请求方式 GET

## 任务
 * 读取接口
	* tasks/show
 * 写入接口
	* tasks/create
		* HTTP请求方式 POST
	* tasks/destroy
		* HTTP请求方式 POST,DELETE
	* tasks/update
		* HTTP请求方式 POST,PUT
 * 数据统计接口
	* tasks/stats
		* HTTP请求方式 GET

## 番茄工作时间段
 * 读取接口
	* tomatos/show
 * 写入接口
	* tomatos/create
	* tomatos/destroy
	* tomatos/update
 * 数据统计接口
	* tomatos/stats

## 数据同步
 * 数据上传同步接口
   * syncUp
 * 数据下载同步接口
   * syncDown
 * 数据双向同步接口
   * syncTwoway
