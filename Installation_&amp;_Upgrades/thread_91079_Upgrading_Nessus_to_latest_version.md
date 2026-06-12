---
title: "Upgrading Nessus to latest version"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by Black Moon on 2005-11-16
Hello everyone, I'm a newly converted long time windows user to linux. I've tried   
 several distro's and found Ubuntu to be the best for me, so i'm here to stay. :) 
  
The promblem i'm having is upgrading nessus to the latest version , which is 2.2.6. I went to Nessus home page and they have two methods to install. Use the  nessus easy installer script. With that I was to download the file and type
 sh nessus-install.sh into terminal. I did that and here's what i got got. 

rob@Black-Star:~$  sh nessus-install.sh
sh: nessus-install.sh: No such file or directory

 The file is in my home directory. Since I could'nt get that method to work I tried the other which is to compile the four files need for installation. They give you the commands to do this on nessus home page i followed the instuctions and got the same error.

rob@Black-Star:~$ cd nessus-libraries
bash: cd: nessus-libraries: No such file or directory

that happened with each file. Here's how the nessus home page said to compile the files. 


    * nessus-libraries-x.x.tar.gz
    * libnasl-x.x.tar.gz
    * nessus-core.x.x.tar.gz
    * nessus-plugins.x.x.tar.gz 

You must compile them in this order.

Installing nessus-libraries

      Compiling nessus-libraries is a simple operation :

cd nessus-libraries
./configure 
make

make install

Installing libnasl

      This is straightforward :

cd libnasl
./configure
make 

      And as root, do :

make install

Repeat the same operation with nessus-core and nessus-plugins.

If you are using Linux, then make sure that /usr/local/lib is in /etc/ld.so.conf, and type ldconfig. Solaris users will have to execute :

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib

Any help with this would be greatly appreciated. I know it's most likely a simple problem but remember i'm a newbie :p

---

