---
title: "High availabilty webserver with GlusterFS and Ucarp"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by skiefta on 2011-11-29
Hello,

Im experiencing some issues with GlusterFS.

I have 2 Ubuntu servers, both installed as webservers.

This commands I used:

apt-get update
apt-get upgrade

apt-get install openssh-server ( so that me and my friend both can work on the same time)
apt-get install apache2 php5 mysql-server phpmyadmin

/etc/init.d/apache2 start
start mysql

So now both servers have a webserver running. what i want to do is set up ucarp. 
Ucarp has it own virtual ipadress. So the client acces the website with that adress and sees the website. When the primairy server is disconnected the secundairy server takes over.

i install ucarp by

apt-get install libibverbs1

apt-get install ucarp

Now I configure the network on the primairy server
cd /etc/network
vim interfaces

iface eth0 inet static
    adress 192.168.1.1
    netmask 255.255.255.0
    ucarp-vid 3
    ucarp-vip 192.168.1.3
    ucarp-password *******
    ucarp-advskew 10
    ucarp-advbase 1
    ucarp-master yes

iface eth0:ucarp inet static
    address 192.168.1.4
    netmask 255.255.255.0

Now i configure the network on the secundairy server
cd /etc/network
vim interfaces

iface eth0 inet static
	adress 192.168.1.2
	netmask 255.255.255.0
	ucarp-vid 3
	ucarp-vip 192.168.1.3
	ucarp-password *******
	ucarp-advskew 10
	ucarp-advbase 1
	ucarp-master no

iface eth0:ucarp inet static
	address 192.168.1.4
	netmask 255.255.255.0

then when i restart my primairy server with
/etc/init.d/networking restart

now the secundairy server takes over the ucarp virtual ip address.

I can check this by entering the command:
ip a show dev eth0   So now when a client goes to the ip adress of ucarp 192.168.1.4  he sees the website of the primairy server. When I change this website and the server fails, the secundairy server takes over but changes made will not show.  So i need glusterFS for replication   I download glusterFS here: wget [http://download.gluster.com/pub/gluster/glusterfs/3.1/LATEST/Ubuntu/glusterfs_3.1.7-1_amd64.deb](http://download.gluster.com/pub/gluster/glusterfs/3.1/LATEST/Ubuntu/glusterfs_3.1.7-1_amd64.deb)  sudo dpkg -i glusterfs*.deb sudo apt-get -f install  In the tutorial i used it says i have to start glusterfs by entering: /etc/init.d/glusterfs start. But in the map init.d there is no glusterfs. Only glusterd. So i started glusterd.  On the primairy server ive entered the command: gluster peer probe 192.168.1.2  and created storage on both servers with: mkdir -p /export/data  gluster volume create datastore replica 2 transport tcp 192.168.1.1:/export/data 192.168.1.2:/export/data  gluster volume start datastore gluster volume info  It says replica is started and lists both ip adress of both servers.   I now want to put the index.html from apache in this replicated folder in both servers. So when the primairy server is onn he will use the index.html in the /export/data. But when he fails the secundairy server takes over and he to will take the index.html from his /export/data.  Can someone please help me? I appreciate ANY help!!

---

### Post by philobyte on 2012-04-01
fwiw, the address in the eth0:ucarp stanza is supposed to be the same as the ucarp-vip, aaccoding to the example in /usr/share/doc/ucarp/README.Debian

---

