# LGX C++ WEB SERVER



## Introduction

The lgx server is a high-performance static web server, written by c++ language. If you wanna to handle post or get method of http, you can use c++ language to develop your own server, just develop the src/work/work.hh/cc.



## How to use lgx server

You should make sure you have install compile environment as follows:
### Debian, Ubuntu ....

```
sudo apt install g++
sudo apt install gcc
sudo apt install make
```
### Get open source
Git clone src to compile

```sh
git clone https://github.com/I0gan/lgx.git
cd lgx
```
Now you can compile with make
### Compile
```
make -j 8
```

### Run

```
chmod +x start && ./start
```

 Input ip address or domain you can access web to see as follows:

```
Welcome to use lgx server!
```



## Configure File

The default configure file at bin/etc/config.json, 

If you wanna change default page, you need to change the configure file, default configure file content as follows:

```
{
    "port" : 80,
    "number_of_thread": 8,
    "log_path" : "data/log",
    "root_path" : "www",
    "web_page" : "index.html",
    "web_404_page" : "404.html",
    "log_path" : "./lgx.log",
    "firewall" : {
    }
}
```

port:  server listen port

number_of_thread: your server will run with how many threads, default with 4

log_path: the path of print server log

root_path: the root path of access web

web_page: default access web page file

web_404_page: not found web page file

log_path:  the path of log file

firewall: forbid specific client to access server, for example:

```
"firewall" : {
	"1", "10.1.1.1",
	"2", "101.2.4.5"
 }
```

It means to forbid client with ip address as  "10.1.1.1" or "101.2.4.5" to access server 

If you configured the file,you can restart server directly, not to recomplie the server again!



## Dev Log

2020-04-...   : Create a server multi-threads and epoll event framework

2020-08-26  : Create a github repositories

2020-09-21 : Add firewall to forbid specific  ip address to access server

2020-09-25: Add logger module

2020-09-28: Make lgx server security quit when press ctrl + c.

2020-09-30: Fix memory leak when ctrl + c and add a cypto module to decode url code

2020-10-03: Fix server breakdown when access web frequently (BUG: The log module is not synchronized)

2020-10-16: Set logger module  thread blocking avoids a lot of CPU usage

2020-10-16: Add a sqlite database module

2020-10-18: Reinforced firewall function (website has been attacked, detailed in CVE-2020-1018 )

2020-11-10: Replace type of http recv buffer  to lgx::util::vessel, so it's faster than std::string when recv data



## LGX CVE LIST

[LIST](./vuls/cve.md)



## Src Tree

```
src
├── base.hh
├── crypto
│   └── url.hh
├── db
│   ├── mysql
│   │   ├── query.cc
│   │   ├── query.hh
│   │   ├── sql.cc
│   │   └── sql.hh
│   └── sqlite
│       ├── query.cc
│       ├── query.hh
│       ├── sql.cc
│       └── sql.hh
├── log
│   ├── log.cc
│   ├── log.hh
│   ├── log_thread.cc
│   └── log_thread.hh
├── main.cc
├── net
│   ├── channel.cc
│   ├── channel.hh
│   ├── epoll.cc
│   ├── epoll.hh
│   ├── eventloop.cc
│   ├── eventloop.hh
│   ├── eventloop_thread.cc
│   ├── eventloop_thread.hh
│   ├── eventloop_threadpool.cc
│   ├── eventloop_threadpool.hh
│   ├── http.cc
│   ├── http.hh
│   ├── net.cc
│   ├── net.hh
│   ├── timer.cc
│   ├── timer.hh
│   ├── util.cc
│   └── util.hh
├── security
│   ├── firewall.cc
│   └── firewall.hh
├── start_up.cc
├── start_up.hh
├── third
│   ├── json.hh
│   ├── sqlite3.c
│   └── sqlite3.h
├── thread
│   ├── condition.hh
│   ├── count_down_latch.hh
│   ├── mutex_lock.hh
│   ├── noncopyable.hh
│   ├── thread.cc
│   └── thread.hh
├── util
│   ├── util.cc
│   ├── util.hh
│   └── vessel.hh
└── work
    ├── work.cc
    └── work.hh

```



## About Author

Name: `I0gan` 

QQ: `418894113`

Email: `l418894113@gmail.com`

Web: http://i0gan.cn

Blog: http://blog.i0gan.cn



## Feedback

If you have found any vulnerability in lgx source code, welcome to feedback by sending email to  `l418894113@gmail.com` 

### Example

[i0gan.cn](http://i0gan.cn)
