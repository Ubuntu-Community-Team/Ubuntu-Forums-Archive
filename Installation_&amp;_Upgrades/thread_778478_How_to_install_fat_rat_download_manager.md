---
title: "How to install fat rat download manager???"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by rado3105 on 2008-05-02
Hi there is very interesting download manager out called FatRat, and I have no idea how to install it, can you make detailed explanation? 
I downloaded tarbal files from: [http://www.dolezel.info/download/data/fatrat/fatrat-svn-20080502.tar.bz2](http://www.dolezel.info/download/data/fatrat/fatrat-svn-20080502.tar.bz2)

Here is manual: [http://fatrat.dolezel.info/content/view/13/28/lang,en/](http://fatrat.dolezel.info/content/view/13/28/lang,en/)
but I dont understand that installation.

---

### Post by renzokuken on 2008-05-02
first install the dependencies (i'm assuming your are using Hardy 8.04)

```
sudo apt-get install libssh-2 libqt4-core libtorrent11 build-essential
```

then download the tarbal from the link in your post, open a terminal and do the following

extract the tarball
```
tar xjf fatrat*
```

enter the directory
```
cd fatrat*
```

now build the source, running each command one at a time
```
cmake . -DWITH_BITTORRENT=ON -DWITH_SFTP=ON -DWITH_JABBER=ON -DWITH_NLS=ON
make
sudo make install
```

---

### Post by rado3105 on 2008-05-03
It doesnt work, it writes Qt qmake not found!

> r-c@r-c-laptop:~/Plocha/fatrat-svn-20080503$ cmake . -DWITH_BITTORRENT=ON -DWITH_SFTP=ON -DWITH_JABBER=ON -DWITH_NLS=ON
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
CMake Error: Qt qmake not found!
-- Configuring done
r-c@r-c-laptop:~/Plocha/fatrat-svn-20080503$ make
make: *** No targets specified and no makefile found.  Stop.
r-c@r-c-laptop:~/Plocha/fatrat-svn-20080503$ 
r-c@r-c-laptop:~/Plocha/fatrat-svn-20080503$ sudo make install
[sudo] password for r-c: 
make: *** No rule to make target `install'.  Stop.
r-c@r-c-laptop:~/Plocha/fatrat-svn-20080503$ 

---

### Post by robertchahine on 2008-05-03
```

sudo apt-get install qt
```
to install qt

or download it from here
[http://trolltech.com/developer/downloads/qt/x11](http://trolltech.com/developer/downloads/qt/x11)

---

### Post by rado3105 on 2008-05-03
>  Found Qt-Version 4.3.4
-- LIBTORRENT was not found. Make sure LIBTORRENT_LIBRARY and LIBTORRENT_INCLUDE_DIR are set.
CMake Error: No Rasterbar libtorrent
-- Configuring done


HOw to solve this problem??

---

### Post by darcio53 on 2008-09-16
Hello

[http://hydr0g3n.free.fr/ubuntu/dists/hardy/main/binary-i386/libs/libtorrent-rasterbar0_0.13.1-2ubuntu1_i386.deb](http://hydr0g3n.free.fr/ubuntu/dists/hardy/main/binary-i386/libs/libtorrent-rasterbar0_0.13.1-2ubuntu1_i386.deb) and libtorrent-rasterbar-dev_0.13.1-2ubuntu1_i386.deb from qbittorrent website

Bye

---

### Post by myidbe on 2008-09-18
The following will install libtorrent-dev using the ubuntu repositories (which is generally recommended).

```
sudo apt-get install libtorrent-dev
```

Retry your cmake afterwards..

---

### Post by Partyboi2 on 2008-09-18
I agree with darcio53, you need to install libtorrent-rasterbar-dev package which is not in the hardy repo.

---

### Post by rado3105 on 2008-09-27
It showed me this and still doesnt want to install:

> r-c@r-c-desktop:~/Plocha/fatrat-1.1$ cmake . -DWITH_BITTORRENT=ON -DWITH_SFTP=ON
-- libtorrent found OK /usr/lib/libtorrent-rasterbar.so
-- ASIO was not found. Make sure ASIO_INCLUDE_DIR is set.
CMake Error at CMakeLists.txt:44 (message):
  No Boost asio


---

### Post by Partyboi2 on 2008-09-27
Try installing libasio-dev

---

### Post by rado3105 on 2008-09-28
after installing libasio-dev:
 > GLOOX was not found. Make sure GLOOX_LIBRARY and GLOOX_INCLUDE_DIR are set.
CMake Error at CMakeLists.txt:58 (message):
  No gloox


-- Configuring done


---

### Post by Partyboi2 on 2008-09-28
try installing libgloox-dev


[B]
[/B]

---

### Post by rado3105 on 2008-09-28
after installing libgloogx, i could use make, but another problem:
> [ 71%] Building CXX object CMakeFiles/fatrat.dir/src/tools/CreateTorrentDlg.cpp.o
In file included from /usr/include/boost/multi_index/detail/node_type.hpp:23,
                 from /usr/include/boost/multi_index/detail/index_base.hpp:21,
                 from /usr/include/boost/multi_index/detail/base_type.hpp:21,
                 from /usr/include/boost/multi_index_container.hpp:32,
                 from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index/detail/index_node_base.hpp:22:42: error: boost/serialization/access.hpp: No such file or directory
In file included from /usr/include/boost/multi_index/detail/index_base.hpp:27,
                 from /usr/include/boost/multi_index/detail/base_type.hpp:21,
                 from /usr/include/boost/multi_index_container.hpp:32,
                 from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index/detail/index_loader.hpp:21:39: error: boost/serialization/nvp.hpp: No such file or directory
In file included from /usr/include/boost/multi_index_container.hpp:46,
                 from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index/detail/archive_constructed.hpp:19:49: error: boost/serialization/serialization.hpp: No such file or directory
In file included from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index_container.hpp:48:48: error: boost/serialization/split_member.hpp: No such file or directory
In file included from /usr/include/boost/multi_index/detail/node_type.hpp:23,
                 from /usr/include/boost/multi_index/detail/index_base.hpp:21,
                 from /usr/include/boost/multi_index/detail/base_type.hpp:21,
                 from /usr/include/boost/multi_index_container.hpp:32,
                 from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index/detail/index_node_base.hpp:72: error: ‘boost::serialization’ has not been declared
/usr/include/boost/multi_index/detail/index_node_base.hpp:72: error: friend declaration does not name a class or function
In file included from /usr/include/boost/multi_index/detail/index_base.hpp:27,
                 from /usr/include/boost/multi_index/detail/base_type.hpp:21,
                 from /usr/include/boost/multi_index_container.hpp:32,
                 from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index/detail/index_loader.hpp: In member function ‘void boost::multi_index::detail::index_loader<Node, FinalNode, Allocator>::add(Node*, Archive&, unsigned int)’:
/usr/include/boost/multi_index/detail/index_loader.hpp:49: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index/detail/index_loader.hpp: In member function ‘void boost::multi_index::detail::index_loader<Node, FinalNode, Allocator>::add_track(Node*, Archive&, unsigned int)’:
/usr/include/boost/multi_index/detail/index_loader.hpp:56: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index/detail/index_loader.hpp: In member function ‘FinalNode* boost::multi_index::detail::index_loader<Node, FinalNode, Allocator>::unchecked_load_node(Archive&) const’:
/usr/include/boost/multi_index/detail/index_loader.hpp:104: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index/detail/index_loader.hpp: In member function ‘FinalNode* boost::multi_index::detail::index_loader<Node, FinalNode, Allocator>::load_node(Archive&) const’:
/usr/include/boost/multi_index/detail/index_loader.hpp:112: error: ‘serialization’ has not been declared
In file included from /usr/include/boost/multi_index/detail/index_base.hpp:28,
                 from /usr/include/boost/multi_index/detail/base_type.hpp:21,
                 from /usr/include/boost/multi_index_container.hpp:32,
                 from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index/detail/index_saver.hpp: In member function ‘void boost::multi_index::detail::index_saver<Node, Allocator>::add(Node*, Archive&, unsigned int)’:
/usr/include/boost/multi_index/detail/index_saver.hpp:46: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index/detail/index_saver.hpp: In member function ‘void boost::multi_index::detail::index_saver<Node, Allocator>::add_track(Node*, Archive&, unsigned int)’:
/usr/include/boost/multi_index/detail/index_saver.hpp:53: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index/detail/index_saver.hpp: In static member function ‘static void boost::multi_index::detail::index_saver<Node, Allocator>::save_node(Node*, Archive&)’:
/usr/include/boost/multi_index/detail/index_saver.hpp:123: error: ‘serialization’ has not been declared
In file included from /usr/include/boost/multi_index_container.hpp:46,
                 from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index/detail/archive_constructed.hpp: In constructor ‘boost::multi_index::detail::archive_constructed<T>::archive_constructed(Archive&, unsigned int)’:
/usr/include/boost/multi_index/detail/archive_constructed.hpp:37: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index/detail/archive_constructed.hpp: In constructor ‘boost::multi_index::detail::archive_constructed<T>::archive_constructed(const char*, Archive&, unsigned int)’:
/usr/include/boost/multi_index/detail/archive_constructed.hpp:51: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index/detail/archive_constructed.hpp:53: error: ‘serialization’ has not been declared
In file included from /usr/include/libtorrent/file_pool.hpp:41,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index_container.hpp: At global scope:
/usr/include/boost/multi_index_container.hpp:564: error: ‘boost::serialization’ has not been declared
/usr/include/boost/multi_index_container.hpp:564: error: friend declaration does not name a class or function
/usr/include/boost/multi_index_container.hpp:568: error: expected ‘;’ before ‘typedef’
/usr/include/boost/multi_index_container.hpp: In member function ‘void boost::multi_index::multi_index_container<Value, IndexSpecifierList, Allocator>::save(Archive&, unsigned int) const’:
/usr/include/boost/multi_index_container.hpp:575: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index_container.hpp:576: error: ‘index_saver_type’ was not declared in this scope
/usr/include/boost/multi_index_container.hpp:576: error: expected `;' before ‘sm’
/usr/include/boost/multi_index_container.hpp:579: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index_container.hpp:580: error: ‘sm’ was not declared in this scope
/usr/include/boost/multi_index_container.hpp:582: error: ‘sm’ was not declared in this scope
/usr/include/boost/multi_index_container.hpp: In member function ‘void boost::multi_index::multi_index_container<Value, IndexSpecifierList, Allocator>::load(Archive&, unsigned int)’:
/usr/include/boost/multi_index_container.hpp:595: error: ‘serialization’ has not been declared
In file included from /usr/include/boost/multi_index/ordered_index.hpp:51,
                 from /usr/include/libtorrent/file_pool.hpp:43,
                 from /home/r-c/Plocha/fatrat-1.1/src/tools/CreateTorrentDlg.cpp:34:
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp: At global scope:
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp:77: error: expected ‘;’ before ‘typedef’
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp: In member function ‘void boost::multi_index::detail::bidir_node_iterator<Node, Derived>::save(Archive&, unsigned int) const’:
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp:82: error: ‘node_base_type’ was not declared in this scope
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp:82: error: ‘bnode’ was not declared in this scope
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp:83: error: ‘serialization’ has not been declared
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp: In member function ‘void boost::multi_index::detail::bidir_node_iterator<Node, Derived>::load(Archive&, unsigned int)’:
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp:89: error: ‘node_base_type’ was not declared in this scope
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp:89: error: ‘bnode’ was not declared in this scope
/usr/include/boost/multi_index/detail/bidir_node_iterator.hpp:90: error: ‘serialization’ has not been declared
make[2]: *** [CMakeFiles/fatrat.dir/src/tools/CreateTorrentDlg.cpp.o] Error 1
make[1]: *** [CMakeFiles/fatrat.dir/all] Error 2
make: *** [all] Error 2
r-c@r-c-desktop:~/Plocha/fatrat-1.1$ 

---

### Post by ibs on 2008-09-28
When i run the make command when trying to install FatRat i get this error:

> 

[  0%] Building CXX object CMakeFiles/fatrat.dir/src/engines/RapidshareUpload.cpp.o
/home/ibs/fatrat-1.1/src/engines/RapidshareUpload.cpp: In member function ‘void RapidshareUpload::beginNextChunk()’:
/home/ibs/fatrat-1.1/src/engines/RapidshareUpload.cpp:371: error: ‘CURLFORM_STREAM’ was not declared in this scope
make[2]: *** [CMakeFiles/fatrat.dir/src/engines/RapidshareUpload.cpp.o] Error 1
make[1]: *** [CMakeFiles/fatrat.dir/all] Error 2
make: *** [all] Error 2



---

### Post by Partyboi2 on 2008-09-29
> **rado3105 said:**
> after installing libgloogx, i could use make, but another problem:
looks like you may also need to install libboost-serialization-dev if you have not already got it installed.

---

### Post by Partyboi2 on 2008-09-29
> **ibs said:**
> When i run the make command when trying to install FatRat i get this error:
That error refers to libcurl, have you got libcurl installed?

---

### Post by ibs on 2008-09-29
> **Partyboi2 said:**
> That error refers to libcurl, have you got libcurl installed?

Yes i have libcurl installed

---

### Post by rado3105 on 2008-09-29
after make it stopped here:
> [ 28%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentSettings.cxx.o
[ 29%] Building CXX object CMakeFiles/fatrat.dir/src/remote/moc_JabberService.cxx.o
[ 29%] Building CXX object CMakeFiles/fatrat.dir/src/remote/moc_SettingsJabberForm.cxx.o
[ 30%] Building CXX object CMakeFiles/fatrat.dir/qrc_resources.cxx.o
Linking CXX executable fatrat
[100%] Built target fatrat

but I cant start fatrat in terminal and seems that its not installed

---

### Post by Partyboi2 on 2008-09-29
> **rado3105 said:**
> after make it stopped here:


but I cant start fatrat in terminal and seems that its not installed
Did you ```
sudo make install
```

---

### Post by rado3105 on 2008-09-29
Thanks a lot, after sudo make install works great, BIG THANKS

---

### Post by Partyboi2 on 2008-09-29
> **ibs said:**
> Yes i have libcurl installed
What version of libcurl are you using? Maybe try installing a later version of libcurl.
[http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)

---

### Post by ibs on 2008-09-29
Installing the latest curl from source did the trick. Thanks!

> **Partyboi2 said:**
> What version of libcurl are you using? Maybe try installing a later version of libcurl.
[http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)

---

### Post by ilhuns on 2008-10-14
Hi i'm trying install fatrat but i live problem and see this message

```
[ 52%] Building CXX object CMakeFiles/fatrat.dir/src/Queue.cpp.o
/home/ilhuns/Desktop/fatrat-1.1/src/Queue.cpp:34: error: ‘Recursive’ is not a member of ‘QReadWriteLock’
/home/ilhuns/Desktop/fatrat-1.1/src/Queue.cpp: In constructor ‘Queue::Queue()’:
/home/ilhuns/Desktop/fatrat-1.1/src/Queue.cpp:38: error: ‘Recursive’ is not a member of ‘QReadWriteLock’
make[2]: *** [CMakeFiles/fatrat.dir/src/Queue.cpp.o] Error 1
make[1]: *** [CMakeFiles/fatrat.dir/all] Error 2
make: *** [all] Error 2

```

How to solve this problem?

---

### Post by aenesias on 2008-11-15
i am using intrepid i have installed everything written in this topic so far but i am still getting this error
```
CMake Error at /usr/share/cmake-2.6/Modules/FindQt4.cmake:1472 (MESSAGE):
  Qt qmake not found!
Call Stack (most recent call first):
  CMakeLists.txt:8 (find_package)

```

---

### Post by Partyboi2 on 2008-11-16
> **aenesias said:**
> i am using intrepid i have installed everything written in this topic so far but i am still getting this error
```
CMake Error at /usr/share/cmake-2.6/Modules/FindQt4.cmake:1472 (MESSAGE):
  Qt qmake not found!
Call Stack (most recent call first):
  CMakeLists.txt:8 (find_package)

```
Try installing the libqt4-dev package
```
sudo apt-get install libqt4-dev 
```

---

### Post by aenesias on 2008-11-16
> **Partyboi2 said:**
> Try installing the libqt4-dev package
```
sudo apt-get install libqt4-dev 
```

Thank u so much it worked

---

### Post by joshuaboshi on 2009-01-15
Hi! 
I am trying to compile fatrat 1.1 on ubuntu 8.04.. and I am still getting this error:

```
src/Queue.cpp:34: error: ‘Recursive’ is not a member of ‘QReadWriteLock’

[15:09:04] Josh: [ 51%] Building CXX object CMakeFiles/fatrat.dir/src/Queue.cpp.o
/home/joshua/fatrat-1.1/src/Queue.cpp:34: error: ‘Recursive’ is not a member of ‘QReadWriteLock’
/home/joshua/fatrat-1.1/src/Queue.cpp: In constructor ‘Queue::Queue()’:
/home/joshua/fatrat-1.1/src/Queue.cpp:38: error: ‘Recursive’ is not a member of ‘QReadWriteLock’
make[2]: *** [CMakeFiles/fatrat.dir/src/Queue.cpp.o] Error 1
make[1]: *** [CMakeFiles/fatrat.dir/all] Error 2
make: *** [all] Error 2
```

I tried to install libqt4-dev as you proposed, but with no effect. 
Thanks for any advice...
Josh

---

### Post by rado3105 on 2009-01-15
I installed it on ubuntu 8.10 this way:
- with support for RS premium accounts

> sudo apt-get install qt4-dev-tools 

sudo apt-get install libssh-2 libqt4-core libtorrent11 build-essential

sudo apt-get install libtorrent-rasterbar-dev

sudo apt-get install libgloox-dev

sudo apt-get install libcurl4-openssl-dev

sudo cmake . -DWITH_BITTORRENT=ON -DWITH_SFTP=ON -DWITH_CURL=ON

sudo make

sudo make install

-DWITH_CURL=ON, and also sudo apt-get install libcurl4-openssl-dev needed only if you  want RS support. There are many variables see original page: dolezel.info

---

### Post by FZ44 on 2009-10-17
Hi, I am trying to install FatRat too

>>>When I do cmake I get this error:

ben@ben-desktop:~/fatrat-1.1$ sudo cmake . -DWITH_BITTORRENT=ON -DWITH_SFTP=ON -DWITH_CURL=ON
-- libtorrent found OK /usr/lib/libtorrent-rasterbar.so
-- ASIO was not found. Make sure ASIO_INCLUDE_DIR is set.
CMake Error at CMakeLists.txt:44 (message):
  No Boost asio


-- Configuring incomplete, errors occurred!

>>>So, I figure that I need libasio??, but get an error :confused::

ben@ben-desktop:~/fatrat-1.1$ sudo apt-get install libasio-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libasio-dev: Depends: libboost1.35-dev but it is not going to be installed or
                        libboost-dev
               Depends: libboost-date-time1.35-dev but it is not going to be installed or
                        libboost-date-time-dev but it is not going to be installed
               Recommends: libboost-regex1.35-dev but it is not going to be installed or
                           libboost-regex-dev but it is not going to be installed
E: Broken packages

Can someone help me out? I am very new to Linux
Thanks

---

### Post by FZ44 on 2009-10-18
bump.

---

### Post by Boris911 on 2009-11-22
I have problem with start fatrat on text-server mode. I establish my Home-Server on Ubuntu Server 9.10. I did this steps:

apt-get install qt4-dev-tools
apt-get install libssh-2 libqt4-core libtorrent11 build-essential
apt-get install libtorrent-rasterbar-dev
apt-get install libgloox-dev
apt-get install libcurl4-openssl-dev
apt-get install xserver-xorg-core
apt-get install cmake
cd /mnt/DATA1/fatrat/
cmake . -DWITH_BITTORRENT=ON -DWITH_SFTP=ON -DWITH_CURL=ON -DWITH_WEBINTERFACE=ON
make
.
.
.
(it was too long for Putty history)
.
Linking CXX executable fatrat
[100%] Built target fatrat
root@HOME-SERVER:/mnt/DATA1/fatrat# make install
[100%] Built target fatrat
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/share/fatrat/LICENSE
-- Installing: /usr/local/share/fatrat/TRANSLATIONS
-- Installing: /usr/local/share/fatrat/README
-- Installing: /usr/local/share/fatrat/AUTHORS
-- Installing: /usr/local/share/fatrat/INSTALL
-- Installing: /usr/local/share/fatrat/data/defaults.conf
-- Installing: /usr/local/share/fatrat/data/css/queueview.css
-- Installing: /usr/local/share/fatrat/data/css/label-headers.css
-- Installing: /usr/local/share/pixmaps/fatrat.png
-- Installing: /usr/local/share/applications/fatrat.desktop
-- Installing: /usr/local/include/fatrat/fatrat.h
-- Installing: /usr/local/include/fatrat/AppTools.h
-- Installing: /usr/local/include/fatrat/Transfer.h
-- Installing: /usr/local/include/fatrat/WidgetHostChild.h
-- Installing: /usr/local/include/fatrat/WidgetHostDlg.h
-- Installing: /usr/local/include/fatrat/Queue.h
-- Installing: /usr/local/include/fatrat/Logger.h
-- Installing: /usr/local/include/fatrat/RuntimeException.h
-- Installing: /usr/local/include/fatrat/Settings.h
-- Installing: /usr/local/include/fatrat/Auth.h
-- Installing: /usr/local/include/fatrat/Proxy.h
-- Installing: /usr/local/include/fatrat/XmlRpc.h
-- Installing: /usr/local/include/fatrat/engines/CurlDownload.h
-- Installing: /usr/local/include/fatrat/engines/CurlUser.h
-- Installing: /usr/local/include/fatrat/engines/CurlPoller.h
-- Installing: /usr/local/include/fatrat/engines/OutputBuffer.h
-- Installing: /usr/local/include/fatrat/engines/CurlStat.h
-- Installing: /usr/local/include/fatrat/poller/Poller.h
-- Installing: /usr/local/share/fatrat/lang/fatrat_cs_CZ.qm
-- Installing: /usr/local/share/fatrat/lang/fatrat_pl_PL.qm
-- Installing: /usr/local/share/fatrat/lang/fatrat_tr_TR.qm
-- Installing: /usr/local/share/fatrat/lang/fatrat_sk_SK.qm
-- Installing: /usr/local/share/fatrat/data/btsearch.xml
-- Installing: /usr/local/share/fatrat/data/btlinks.txt
-- Installing: /usr/local/share/fatrat/data/remote/reload.png
-- Installing: /usr/local/share/fatrat/data/remote/download.png
-- Installing: /usr/local/share/fatrat/data/remote/header.png
-- Installing: /usr/local/share/fatrat/data/remote/favicon.png
-- Installing: /usr/local/share/fatrat/data/remote/logo.png
-- Installing: /usr/local/share/fatrat/data/remote/toolbar.png
-- Installing: /usr/local/share/fatrat/data/remote/down.png
-- Installing: /usr/local/share/fatrat/data/remote/delete.png
-- Installing: /usr/local/share/fatrat/data/remote/graph.png
-- Installing: /usr/local/share/fatrat/data/remote/upload.png
-- Installing: /usr/local/share/fatrat/data/remote/browse.png
-- Installing: /usr/local/share/fatrat/data/remote/add.png
-- Installing: /usr/local/share/fatrat/data/remote/delete_with_data.png
-- Installing: /usr/local/share/fatrat/data/remote/browse.qsp
-- Installing: /usr/local/share/fatrat/data/remote/add_transfer2.qsp
-- Installing: /usr/local/share/fatrat/data/remote/details.qsp
-- Installing: /usr/local/share/fatrat/data/remote/add_transfer.qsp
-- Installing: /usr/local/share/fatrat/data/remote/queue.qsp
-- Installing: /usr/local/share/fatrat/data/remote/index.qsp
-- Installing: /usr/local/share/fatrat/data/remote/index.js
-- Installing: /usr/local/share/fatrat/data/remote/style.css
-- Installing: /usr/local/share/fatrat/data/remote/move/up.png
-- Installing: /usr/local/share/fatrat/data/remote/move/bottom.png
-- Installing: /usr/local/share/fatrat/data/remote/move/down.png
-- Installing: /usr/local/share/fatrat/data/remote/move/top.png
-- Installing: /usr/local/share/fatrat/data/remote/queue/remove.png
-- Installing: /usr/local/share/fatrat/data/remote/queue/properties.png
-- Installing: /usr/local/share/fatrat/data/remote/queue/add.png
-- Installing: /usr/local/share/fatrat/data/remote/states/paused_upload.png
-- Installing: /usr/local/share/fatrat/data/remote/states/waiting_upload.png
-- Installing: /usr/local/share/fatrat/data/remote/states/active_upload.png
-- Installing: /usr/local/share/fatrat/data/remote/states/completed_upload.png
-- Installing: /usr/local/share/fatrat/data/remote/states/active.png
-- Installing: /usr/local/share/fatrat/data/remote/states/paused.png
-- Installing: /usr/local/share/fatrat/data/remote/states/completed.png
-- Installing: /usr/local/share/fatrat/data/remote/states/forcedactive_upload.png
-- Installing: /usr/local/share/fatrat/data/remote/states/failed.png
-- Installing: /usr/local/share/fatrat/data/remote/states/waiting.png
-- Installing: /usr/local/share/fatrat/data/remote/states/forcedactive.png
-- Installing: /usr/local/share/fatrat/data/remote/states/failed_upload.png
-- Installing: /usr/local/share/fatrat/data/remote/filedialog/ajaxrequest.qsp
-- Installing: /usr/local/share/fatrat/data/remote/filedialog/api.js
-- Installing: /usr/local/share/fatrat/data/remote/filedialog/minus.png
-- Installing: /usr/local/share/fatrat/data/remote/filedialog/dirdialog.html
-- Installing: /usr/local/share/fatrat/data/remote/filedialog/plus.png
-- Installing: /usr/local/share/man/man1/fatrat.1
-- Installing: /usr/local/bin/fatrat
root@HOME-SERVER:/mnt/DATA1/fatrat# fatrat --nogui
Current locale "en_US"
Segmentation fault
root@HOME-SERVER:/mnt/DATA1/fatrat#

I have only text mode. But fatrat don't want to run with out GUI. Where should be problem? Firewall is turn off, because I can't set up it. And when I write [http://HOME-SERVER:2233/](http://HOME-SERVER:2233/) I got no response. Webmin is working on port 10000. 

I thank you for your ideas before.

---

### Post by lubramb on 2010-03-04
Hi all,

following this post i'm finally able to install fatrat, but i have a big problem.

I'm new in linux world (i'm install it first time 2 weeks ago), and my question is:

Where i must go to run Fatrat???

[spoiler]luca@luca-ubuntu:~/Scaricati/fatrat-1.1.2$ cmake . -DWITH_BITTORRENT=ON -DWITH_SFTP=ON -DWITH_CURL=ON -DWITH_WEBINTERFACE=ON

-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Boost version: 1.38.0
-- Found the following Boost libraries:
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.5.2
-- checking for module 'libtorrent-rasterbar >= 0.14.6'
--   found libtorrent-rasterbar , version 0.14.6
-- libtorrent found OK
-- Boost version: 1.38.0
-- Found the following Boost libraries:
--   date_time
-- boost-datetime found OK
-- checking for module 'libcurl >= 7.18.2'
--   found libcurl , version 7.19.5
-- Looking for include files HAVE_SYS_EPOLL_H
-- Looking for include files HAVE_SYS_EPOLL_H - found
-- Looking for kqueue
-- Looking for kqueue - not found
-- Configuring done
-- Generating done
-- Build files have been written to: /home/luca/Scaricati/fatrat-1.1.2
luca@luca-ubuntu:~/Scaricati/fatrat-1.1.2$ make
[  1%] Generating fatrat_fr_FR.qm
Updating '/home/luca/Scaricati/fatrat-1.1.2/fatrat_fr_FR.qm'...
    Generated 727 translation(s) (727 finished and 0 unfinished)
[  1%] Generating src/dbus/moc_DbusAdaptor.cxx
[  2%] Generating src/dbus/moc_DbusImpl.cxx
[  2%] Generating src/moc_TransfersModel.cxx
[  2%] Generating src/moc_QueueDlg.cxx
[  3%] Generating src/moc_QueueMgr.cxx
[  3%] Generating src/moc_SpeedGraph.cxx
[  4%] Generating src/moc_SettingsDropBoxForm.cxx
[  4%] Generating src/moc_SettingsNetworkForm.cxx
[  4%] Generating src/moc_SettingsQueueForm.cxx
[  5%] Generating src/moc_SettingsSchedulerForm.cxx
[  5%] Generating src/moc_ScheduledActionDlg.cxx
[  6%] Generating src/moc_StatsWidget.cxx
[  6%] Generating src/moc_ProxyDlg.cxx
[  6%] Generating src/moc_SpeedLimitWidget.cxx
[  7%] Generating src/moc_LogManager.cxx
[  7%] Generating src/moc_SettingsGeneralForm.cxx
[  8%] Generating src/moc_Transfer.cxx
[  8%] Generating src/moc_Scheduler.cxx
[  8%] Generating src/moc_SimpleEmail.cxx
[  9%] Generating src/moc_QueueView.cxx
[  9%] Generating src/moc_MainWindow.cxx
[  9%] Generating src/moc_AboutDlg.cxx
[ 10%] Generating src/moc_SettingsDlg.cxx
[ 10%] Generating src/moc_TransfersView.cxx
[ 11%] Generating src/moc_Queue.cxx
[ 11%] Generating src/moc_MainTab.cxx
[ 11%] Generating src/moc_DropBox.cxx
[ 12%] Generating src/moc_InfoBar.cxx
[ 12%] Generating src/moc_GenericOptsForm.cxx
[ 13%] Generating src/moc_WidgetHostDlg.cxx
[ 13%] Generating src/moc_UserAuthDlg.cxx
[ 13%] Generating src/moc_NewTransferDlg.cxx
[ 14%] Generating src/moc_Logger.cxx
[ 14%] Generating src/moc_MyApplication.cxx
[ 14%] Generating src/moc_ReportBugDlg.cxx
[ 15%] Generating src/engines/moc_OutputBuffer.cxx
[ 15%] Generating src/tools/moc_HashDlg.cxx
[ 16%] Generating src/tools/moc_RapidTools.cxx
[ 16%] Generating src/tools/moc_VideoFetcher.cxx
[ 16%] Generating src/rss/moc_RssFetcher.cxx
[ 17%] Generating src/rss/moc_SettingsRssForm.cxx
[ 17%] Generating src/rss/moc_RssFeedDlg.cxx
[ 18%] Generating src/rss/moc_RssRegexpDlg.cxx
[ 18%] Generating src/rss/moc_RssDownloadedDlg.cxx
[ 18%] Generating src/tooltips/moc_QueueToolTip.cxx
[ 19%] Generating src/tooltips/moc_TrayToolTip.cxx
[ 19%] Generating src/tooltips/moc_BaseToolTip.cxx
[ 20%] Generating src/engines/moc_CurlDownload.cxx
[ 20%] Generating src/engines/moc_CurlUpload.cxx
[ 20%] Generating src/engines/moc_HttpFtpSettings.cxx
[ 21%] Generating src/engines/moc_GeneralDownloadForms.cxx
[ 21%] Generating src/engines/moc_RapidshareUpload.cxx
[ 21%] Generating src/engines/moc_RapidshareFreeDownload.cxx
[ 22%] Generating src/engines/moc_RapidshareStatusWidget.cxx
[ 22%] Generating src/tools/moc_TorrentSearch.cxx
[ 23%] Generating src/tools/moc_TorrentWebView.cxx
[ 23%] Generating src/tools/moc_CreateTorrentDlg.cxx
[ 23%] Generating src/tools/moc_ContextListWidget.cxx
[ 24%] Generating src/engines/moc_TorrentDetails.cxx
[ 24%] Generating src/engines/moc_TorrentPeersModel.cxx
[ 25%] Generating src/engines/moc_TorrentDownload.cxx
[ 25%] Generating src/engines/moc_TorrentOptsWidget.cxx
[ 25%] Generating src/engines/moc_TorrentProgressWidget.cxx
[ 26%] Generating src/engines/moc_TorrentPiecesModel.cxx
[ 26%] Generating src/engines/moc_TorrentFilesModel.cxx
[ 27%] Generating src/engines/moc_TorrentSettings.cxx
[ 27%] Generating src/remote/moc_HttpService.cxx
[ 27%] Generating ui_AboutDlg.h
Warning: name gridLayout is already used
[ 28%] Generating ui_AutoActionForm.h
[ 28%] Generating ui_CommentForm.h
[ 28%] Generating ui_GenericOptsForm.h
[ 29%] Generating ui_MainWindow.h
Warning: name layoutWidget is already used
Warning: name gridLayout is already used
Warning: name layoutWidget is already used
Warning: name layoutWidget is already used
[ 29%] Generating ui_NewTransferDlg.h
Warning: name gridLayout is already used
[ 30%] Generating ui_ProxyDlg.h
[ 30%] Generating ui_QueueDlg.h
[ 30%] Generating ui_SettingsDlg.h
[ 31%] Generating ui_SettingsDropBoxForm.h
[ 31%] Generating ui_SettingsGeneralForm.h
[ 32%] Generating ui_SettingsNetworkForm.h
[ 32%] Generating ui_SettingsQueueForm.h
[ 32%] Generating ui_SettingsSchedulerForm.h
[ 33%] Generating ui_ScheduledActionDlg.h
[ 33%] Generating ui_SpeedLimitWidget.h
[ 33%] Generating ui_UserAuthDlg.h
[ 34%] Generating ui_WidgetHostDlg.h
[ 34%] Generating ui_ReportBugDlg.h
[ 35%] Generating ui_HashDlg.h
[ 35%] Generating ui_RapidTools.h
[ 35%] Generating ui_VideoFetcher.h
[ 36%] Generating ui_SettingsRssForm.h
[ 36%] Generating ui_RssFeedDlg.h
[ 37%] Generating ui_RssRegexpDlg.h
Warning: name gridLayout is already used
[ 37%] Generating ui_RssDownloadedDlg.h
[ 37%] Generating ui_RssEpisodeNameDlg.h
[ 38%] Generating ui_FtpUploadOptsForm.h
[ 38%] Generating ui_HttpOptsWidget.h
[ 39%] Generating ui_HttpUrlOptsDlg.h
[ 39%] Generating ui_SettingsHttpForm.h
[ 39%] Generating ui_RapidshareOptsForm.h
[ 40%] Generating ui_RapidshareUploadDetailsForm.h
[ 40%] Generating ui_RapidshareFreeDownloadOptsForm.h
[ 40%] Generating ui_TorrentSearch.h
[ 41%] Generating ui_TorrentWebView.h
[ 41%] Generating ui_CreateTorrentDlg.h
[ 42%] Generating ui_TorrentDetailsForm.h
[ 42%] Generating ui_TorrentOptsWidget.h
[ 42%] Generating ui_SettingsTorrentForm.h
Warning: name gridLayout is already used
[ 43%] Generating ui_SettingsWebForm.h
[ 43%] Generating qrc_resources.cxx
[ 44%] Generating fatrat_cs_CZ.qm
Updating '/home/luca/Scaricati/fatrat-1.1.2/fatrat_cs_CZ.qm'...
    Generated 726 translation(s) (726 finished and 0 unfinished)

    Ignored 1 untranslated source text(s)
[ 44%] Generating fatrat_pl_PL.qm
Updating '/home/luca/Scaricati/fatrat-1.1.2/fatrat_pl_PL.qm'...
    Generated 646 translation(s) (608 finished and 38 unfinished)

    Ignored 81 untranslated source text(s)
[ 44%] Generating fatrat_tr_TR.qm
Updating '/home/luca/Scaricati/fatrat-1.1.2/fatrat_tr_TR.qm'...
    Generated 646 translation(s) (617 finished and 29 unfinished)

    Ignored 81 untranslated source text(s)
[ 45%] Generating fatrat_sk_SK.qm
Updating '/home/luca/Scaricati/fatrat-1.1.2/fatrat_sk_SK.qm'...
    Generated 646 translation(s) (617 finished and 29 unfinished)

    Ignored 81 untranslated source text(s)
[ 45%] Generating fatrat_ru_RU.qm
Updating '/home/luca/Scaricati/fatrat-1.1.2/fatrat_ru_RU.qm'...
    Generated 656 translation(s) (1 finished and 655 unfinished)

    Ignored 71 untranslated source text(s)
Scanning dependencies of target fatrat
[ 45%] Building CXX object CMakeFiles/fatrat.dir/src/Auth.cpp.o
[ 45%] Building CXX object CMakeFiles/fatrat.dir/src/AboutDlg.cpp.o
[ 46%] Building CXX object CMakeFiles/fatrat.dir/src/AppTools.cpp.o
[ 46%] Building CXX object CMakeFiles/fatrat.dir/src/DropBox.cpp.o
[ 46%] Building CXX object CMakeFiles/fatrat.dir/src/fatrat.cpp.o
[ 47%] Building CXX object CMakeFiles/fatrat.dir/src/Proxy.cpp.o
[ 47%] Building CXX object CMakeFiles/fatrat.dir/src/InfoBar.cpp.o
[ 48%] Building CXX object CMakeFiles/fatrat.dir/src/MainTab.cpp.o
[ 48%] Building CXX object CMakeFiles/fatrat.dir/src/MainWindow.cpp.o
[ 48%] Building CXX object CMakeFiles/fatrat.dir/src/NetIface.cpp.o
[ 49%] Building CXX object CMakeFiles/fatrat.dir/src/NewTransferDlg.cpp.o
[ 49%] Building CXX object CMakeFiles/fatrat.dir/src/Queue.cpp.o
[ 50%] Building CXX object CMakeFiles/fatrat.dir/src/QueueMgr.cpp.o
[ 50%] Building CXX object CMakeFiles/fatrat.dir/src/QueueView.cpp.o
[ 50%] Building CXX object CMakeFiles/fatrat.dir/src/SettingsDlg.cpp.o
[ 51%] Building CXX object CMakeFiles/fatrat.dir/src/SettingsGeneralForm.cpp.o
[ 51%] Building CXX object CMakeFiles/fatrat.dir/src/SettingsNetworkForm.cpp.o
[ 51%] Building CXX object CMakeFiles/fatrat.dir/src/SettingsQueueForm.cpp.o
[ 52%] Building CXX object CMakeFiles/fatrat.dir/src/SettingsSchedulerForm.cpp.o
[ 52%] Building CXX object CMakeFiles/fatrat.dir/src/ScheduledActionDlg.cpp.o
[ 53%] Building CXX object CMakeFiles/fatrat.dir/src/SimpleEmail.cpp.o
[ 53%] Building CXX object CMakeFiles/fatrat.dir/src/SpeedGraph.cpp.o
[ 53%] Building CXX object CMakeFiles/fatrat.dir/src/SpeedLimitWidget.cpp.o
[ 54%] Building CXX object CMakeFiles/fatrat.dir/src/StatsWidget.cpp.o
[ 54%] Building CXX object CMakeFiles/fatrat.dir/src/Transfer.cpp.o
[ 55%] Building CXX object CMakeFiles/fatrat.dir/src/TransfersModel.cpp.o
[ 55%] Building CXX object CMakeFiles/fatrat.dir/src/Logger.cpp.o
[ 55%] Building CXX object CMakeFiles/fatrat.dir/src/XmlRpc.cpp.o
[ 56%] Building CXX object CMakeFiles/fatrat.dir/src/Scheduler.cpp.o
[ 56%] Building CXX object CMakeFiles/fatrat.dir/src/MyFileDialog.cpp.o
[ 57%] Building CXX object CMakeFiles/fatrat.dir/src/ReportBugDlg.cpp.o
[ 57%] Building CXX object CMakeFiles/fatrat.dir/src/Settings.cpp.o
[ 57%] Building CXX object CMakeFiles/fatrat.dir/src/QueueDlg.cpp.o
[ 58%] Building CXX object CMakeFiles/fatrat.dir/src/engines/OutputBuffer.cpp.o
[ 58%] Building CXX object CMakeFiles/fatrat.dir/src/poller/Poller.cpp.o
[ 58%] Building CXX object CMakeFiles/fatrat.dir/src/rss/RssFetcher.cpp.o
[ 59%] Building CXX object CMakeFiles/fatrat.dir/src/rss/SettingsRssForm.cpp.o
[ 59%] Building CXX object CMakeFiles/fatrat.dir/src/rss/RssRegexpDlg.cpp.o
[ 60%] Building CXX object CMakeFiles/fatrat.dir/src/rss/RssDownloadedDlg.cpp.o
[ 60%] Building CXX object CMakeFiles/fatrat.dir/src/tooltips/BaseToolTip.cpp.o
[ 60%] Building CXX object CMakeFiles/fatrat.dir/src/tooltips/QueueToolTip.cpp.o
[ 61%] Building CXX object CMakeFiles/fatrat.dir/src/tooltips/TrayToolTip.cpp.o
[ 61%] Building CXX object CMakeFiles/fatrat.dir/src/dbus/DbusAdaptor.cpp.o
[ 62%] Building CXX object CMakeFiles/fatrat.dir/src/dbus/DbusImpl.cpp.o
[ 62%] Building CXX object CMakeFiles/fatrat.dir/src/tools/HashDlg.cpp.o
[ 62%] Building CXX object CMakeFiles/fatrat.dir/src/tools/RapidTools.cpp.o
[ 63%] Building CXX object CMakeFiles/fatrat.dir/src/tools/VideoFetcher.cpp.o
[ 63%] Building CXX object CMakeFiles/fatrat.dir/src/poller/EpollPoller.cpp.o
[ 63%] Building CXX object CMakeFiles/fatrat.dir/src/engines/CurlDownload.cpp.o
[ 64%] Building CXX object CMakeFiles/fatrat.dir/src/engines/CurlUpload.cpp.o
[ 64%] Building CXX object CMakeFiles/fatrat.dir/src/engines/CurlPoller.cpp.o
[ 65%] Building CXX object CMakeFiles/fatrat.dir/src/engines/CurlUser.cpp.o
[ 65%] Building CXX object CMakeFiles/fatrat.dir/src/engines/CurlStat.cpp.o
[ 65%] Building CXX object CMakeFiles/fatrat.dir/src/engines/GeneralDownloadForms.cpp.o
[ 66%] Building CXX object CMakeFiles/fatrat.dir/src/engines/HttpFtpSettings.cpp.o
[ 66%] Building CXX object CMakeFiles/fatrat.dir/src/engines/RapidshareUpload.cpp.o
[ 67%] Building CXX object CMakeFiles/fatrat.dir/src/engines/RapidshareUploadProgress.cpp.o
[ 67%] Building CXX object CMakeFiles/fatrat.dir/src/engines/RapidshareFreeDownload.cpp.o
[ 67%] Building CXX object CMakeFiles/fatrat.dir/src/engines/RapidshareStatusWidget.cpp.o
[ 68%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentDetails.cpp.o
[ 68%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentDownload.cpp.o
/home/luca/Scaricati/fatrat-1.1.2/src/engines/TorrentDownload.cpp:64:3: warning: #warning NDEBUG defined - please always make sure that libtorrent also has NDEBUG defined
/home/luca/Scaricati/fatrat-1.1.2/src/engines/TorrentDownload.cpp: In member function ‘virtual void TorrentDownload::save(QDomDocument&, QDomNode&) const’:
/home/luca/Scaricati/fatrat-1.1.2/src/engines/TorrentDownload.cpp:955: warning: ‘libtorrent::entry libtorrent::torrent_handle::write_resume_data() const’ is deprecated (declared at /usr/include/libtorrent/torrent_handle.hpp:416)
[ 69%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentFilesModel.cpp.o
/home/luca/Scaricati/fatrat-1.1.2/src/engines/TorrentFilesModel.cpp: In member function ‘void TorrentFilesModel::refresh(const libtorrent::bitfield*)’:
/home/luca/Scaricati/fatrat-1.1.2/src/engines/TorrentFilesModel.cpp:164: warning: ‘void libtorrent::torrent_handle::file_progress(std::vector<float, std::allocator<float> >&) const’ is deprecated (declared at /usr/include/libtorrent/torrent_handle.hpp:326)
[ 69%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentOptsWidget.cpp.o
[ 69%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentIPFilter.cpp.o
[ 70%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentPeersModel.cpp.o
[ 70%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentPiecesModel.cpp.o
[ 70%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentProgressWidget.cpp.o
[ 71%] Building CXX object CMakeFiles/fatrat.dir/src/engines/TorrentSettings.cpp.o
[ 71%] Building CXX object CMakeFiles/fatrat.dir/src/tools/TorrentSearch.cpp.o
[ 72%] Building CXX object CMakeFiles/fatrat.dir/src/tools/TorrentWebView.cpp.o
[ 72%] Building CXX object CMakeFiles/fatrat.dir/src/tools/CreateTorrentDlg.cpp.o
[ 72%] Building CXX object CMakeFiles/fatrat.dir/src/tools/ContextListWidget.cpp.o
[ 73%] Building CXX object CMakeFiles/fatrat.dir/src/remote/HttpService.cpp.o
/home/luca/Scaricati/fatrat-1.1.2/src/remote/HttpService.cpp: In member function ‘void HttpService::serveClient(int)’:
/home/luca/Scaricati/fatrat-1.1.2/src/remote/HttpService.cpp:687: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘size_t’
[ 73%] Building CXX object CMakeFiles/fatrat.dir/src/remote/SettingsWebForm.cpp.o
[ 74%] Building CXX object CMakeFiles/fatrat.dir/src/remote/XmlRpcService.cpp.o
[ 74%] Building CXX object CMakeFiles/fatrat.dir/src/dbus/moc_DbusAdaptor.cxx.o
[ 74%] Building CXX object CMakeFiles/fatrat.dir/src/dbus/moc_DbusImpl.cxx.o
[ 75%] Building CXX object CMakeFiles/fatrat.dir/src/moc_TransfersModel.cxx.o
[ 75%] Building CXX object CMakeFiles/fatrat.dir/src/moc_QueueDlg.cxx.o
[ 76%] Building CXX object CMakeFiles/fatrat.dir/src/moc_QueueMgr.cxx.o
[ 76%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SpeedGraph.cxx.o
[ 76%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SettingsDropBoxForm.cxx.o
[ 77%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SettingsNetworkForm.cxx.o
[ 77%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SettingsQueueForm.cxx.o
[ 77%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SettingsSchedulerForm.cxx.o
[ 78%] Building CXX object CMakeFiles/fatrat.dir/src/moc_ScheduledActionDlg.cxx.o
[ 78%] Building CXX object CMakeFiles/fatrat.dir/src/moc_StatsWidget.cxx.o
[ 79%] Building CXX object CMakeFiles/fatrat.dir/src/moc_ProxyDlg.cxx.o
[ 79%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SpeedLimitWidget.cxx.o
[ 79%] Building CXX object CMakeFiles/fatrat.dir/src/moc_LogManager.cxx.o
[ 80%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SettingsGeneralForm.cxx.o
[ 80%] Building CXX object CMakeFiles/fatrat.dir/src/moc_Transfer.cxx.o
[ 81%] Building CXX object CMakeFiles/fatrat.dir/src/moc_Scheduler.cxx.o
[ 81%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SimpleEmail.cxx.o
[ 81%] Building CXX object CMakeFiles/fatrat.dir/src/moc_QueueView.cxx.o
[ 82%] Building CXX object CMakeFiles/fatrat.dir/src/moc_MainWindow.cxx.o
[ 82%] Building CXX object CMakeFiles/fatrat.dir/src/moc_AboutDlg.cxx.o
[ 82%] Building CXX object CMakeFiles/fatrat.dir/src/moc_SettingsDlg.cxx.o
[ 83%] Building CXX object CMakeFiles/fatrat.dir/src/moc_TransfersView.cxx.o
[ 83%] Building CXX object CMakeFiles/fatrat.dir/src/moc_Queue.cxx.o
[ 84%] Building CXX object CMakeFiles/fatrat.dir/src/moc_MainTab.cxx.o
[ 84%] Building CXX object CMakeFiles/fatrat.dir/src/moc_DropBox.cxx.o
[ 84%] Building CXX object CMakeFiles/fatrat.dir/src/moc_InfoBar.cxx.o
[ 85%] Building CXX object CMakeFiles/fatrat.dir/src/moc_GenericOptsForm.cxx.o
[ 85%] Building CXX object CMakeFiles/fatrat.dir/src/moc_WidgetHostDlg.cxx.o
[ 86%] Building CXX object CMakeFiles/fatrat.dir/src/moc_UserAuthDlg.cxx.o
[ 86%] Building CXX object CMakeFiles/fatrat.dir/src/moc_NewTransferDlg.cxx.o
[ 86%] Building CXX object CMakeFiles/fatrat.dir/src/moc_Logger.cxx.o
[ 87%] Building CXX object CMakeFiles/fatrat.dir/src/moc_MyApplication.cxx.o
[ 87%] Building CXX object CMakeFiles/fatrat.dir/src/moc_ReportBugDlg.cxx.o
[ 88%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_OutputBuffer.cxx.o
[ 88%] Building CXX object CMakeFiles/fatrat.dir/src/tools/moc_HashDlg.cxx.o
[ 88%] Building CXX object CMakeFiles/fatrat.dir/src/tools/moc_RapidTools.cxx.o
[ 89%] Building CXX object CMakeFiles/fatrat.dir/src/tools/moc_VideoFetcher.cxx.o
[ 89%] Building CXX object CMakeFiles/fatrat.dir/src/rss/moc_RssFetcher.cxx.o
[ 89%] Building CXX object CMakeFiles/fatrat.dir/src/rss/moc_SettingsRssForm.cxx.o
[ 90%] Building CXX object CMakeFiles/fatrat.dir/src/rss/moc_RssFeedDlg.cxx.o
[ 90%] Building CXX object CMakeFiles/fatrat.dir/src/rss/moc_RssRegexpDlg.cxx.o
[ 91%] Building CXX object CMakeFiles/fatrat.dir/src/rss/moc_RssDownloadedDlg.cxx.o
[ 91%] Building CXX object CMakeFiles/fatrat.dir/src/tooltips/moc_QueueToolTip.cxx.o
[ 91%] Building CXX object CMakeFiles/fatrat.dir/src/tooltips/moc_TrayToolTip.cxx.o
[ 92%] Building CXX object CMakeFiles/fatrat.dir/src/tooltips/moc_BaseToolTip.cxx.o
[ 92%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_CurlDownload.cxx.o
[ 93%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_CurlUpload.cxx.o
[ 93%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_HttpFtpSettings.cxx.o
[ 93%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_GeneralDownloadForms.cxx.o
[ 94%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_RapidshareUpload.cxx.o
[ 94%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_RapidshareFreeDownload.cxx.o
[ 95%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_RapidshareStatusWidget.cxx.o
[ 95%] Building CXX object CMakeFiles/fatrat.dir/src/tools/moc_TorrentSearch.cxx.o
[ 95%] Building CXX object CMakeFiles/fatrat.dir/src/tools/moc_TorrentWebView.cxx.o
[ 96%] Building CXX object CMakeFiles/fatrat.dir/src/tools/moc_CreateTorrentDlg.cxx.o
[ 96%] Building CXX object CMakeFiles/fatrat.dir/src/tools/moc_ContextListWidget.cxx.o
[ 96%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentDetails.cxx.o
[ 97%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentPeersModel.cxx.o
[ 97%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentDownload.cxx.o
[ 98%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentOptsWidget.cxx.o
[ 98%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentProgressWidget.cxx.o
[ 98%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentPiecesModel.cxx.o
[ 99%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentFilesModel.cxx.o
[ 99%] Building CXX object CMakeFiles/fatrat.dir/src/engines/moc_TorrentSettings.cxx.o
[100%] Building CXX object CMakeFiles/fatrat.dir/src/remote/moc_HttpService.cxx.o
[100%] Building CXX object CMakeFiles/fatrat.dir/qrc_resources.cxx.o
Linking CXX executable fatrat
[/spoiler]

this is last report in consolle (after al lib installation).

Where i can launch fatrat now???

---

