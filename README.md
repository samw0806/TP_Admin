<p align="center">
    <img src="https://img.shields.io/badge/Vue-3.2.40-brightgreen.svg"/>
    <img src="https://img.shields.io/badge/Vite-4.0.0-green.svg"/>
    <img src="https://img.shields.io/badge/Element Plus-2.2.27-blue.svg"/>
    <a href="https://gitee.com/youlaitech/youlai-mall" target="_blank">
        <img src="https://gitee.com/youlaiorg/vue3-element-admin/badge/star.svg"/>
    </a> 
    <img src="https://img.shields.io/badge/license-MIT-green.svg"/>
    <a href="https://gitee.com/youlaiorg" target="_blank">
        <img src="https://img.shields.io/badge/Author-有来开源组织-orange.svg"/>
    </a>
</p>
<p align="center">
<a target="_blank" href="http://vue3.youlai.tech">在线预览</a> |  <a target="_blank" href="https://www.youlai.tech/pages/5d571c/">官方文档</a> 
</p>



## 项目启动

1. 安装依赖

    ```bash
    npm install
    ```
2. 启动运行

    ```bash
    npm run dev
    ```
3. 访问测试

   浏览器访问： [http://localhost:3000](http://localhost:3000)

## 项目部署

- 本地打包

  ```
  npm run build:prod
  ```

  生成的静态文件位于项目根目录 `dist` 文件夹下

- 上传文件

  创建 `/mnt/nginx/html` 目录，将打包生成 `dist` 下的所有文件拷贝至此工作目录下

- nginx.cofig 配置

  ```
  server {
      listen     80;
      server_name  localhost;

      location / {
          root /mnt/nginx/html;
          index index.html index.htm;
      }

      # 代理转发请求至网关，prod-api标识解决跨域,vapi.youlai.tech 线上接口地址，注意后面/
      location /prod-api/ {
          proxy_pass http://vapi.youlai.tech/;
      }
  }

  ```
## 本地接口

> 默认使用线上接口，如果你了解一点Java后端SpringBoot，可轻松搭建本地接口环境：

1. 访问后端项目仓库地址：https://gitee.com/youlaiorg/youlai-boot.git

2. 根据项目说明文档 [README.md](https://gitee.com/youlaiorg/youlai-boot#%E9%A1%B9%E7%9B%AE%E8%BF%90%E8%A1%8C) 完成数据库的创建和后端工程的启动；
3. 进入 [vite.config.ts](vite.config.ts) 文件修改代理线上接口地址 http://vapi.youlai.tech 为本地接口地址 http://localhost:8989 即可。



