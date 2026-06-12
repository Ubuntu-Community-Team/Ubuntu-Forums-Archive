---
title: "mysql corrupt after upgrade to Lucid"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by HectorG on 2010-05-16
I have tried reinstalling uninstalling through synaptic and apt-get but It just hangs. 

Here is an example of where it gets stuck with an apt-get autoremove.

I keep getting this message that states I should reinstall before I uninstall but neither of them work. 

I am not sure what to try any more. :confused:


$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B/7,103kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.1.
(Reading database ... 187905 files and directories currently installed.)
Preparing to replace mysql-server-5.1 5.1.41-3ubuntu12 (using .../mysql-server-5.1_5.1.41-3ubuntu12_amd64.deb) ...

It just hangs here.. I have tried leaving it here for almost two days and nothing...

---

### Post by HectorG on 2010-05-16
Here is what happens if I try to update my packages through the update manager. It just hangs after that second screenshot.

---

### Post by HectorG on 2010-05-18
This is where I am at currently

---

### Post by HectorG on 2010-05-18
if I stop mysql I get  a pop up that says

E: /var/cache/apt/archives/mysql-server-5.1_5.1.41-3ubuntu12_amd64.deb: subprocess new pre-installation script returned error exit status 1

---

### Post by HectorG on 2010-05-19
I tried yet again and here is what I get...

This is where the screen shot would go. At the point where it says exit status code 1 I was able to manually stop mysql and then it proceeds only to get stuck again with the following error coming out of a pop up window.

E: /var/cache/apt/archives/mysql-server-5.1_5.1.41-3ubuntu12.1_amd64.deb: subprocess new pre-installation script returned error exit status 1

---

### Post by VDSA on 2010-05-19
I've got the same problem here

---

### Post by cdcooper on 2010-05-20
I worked around this by editing the 
 /var/lib/dpkg/info/mysql-server-5.1.prerm
and
 /var/lib/dpkg/info/mysql-server-5.1.postinst
files, replacing the code to stop and start mysql (which seemed to be hanging):

	#stop mysql || :
	service mysql stop

and
	#start mysql || :
	service mysql start

---

### Post by HectorG on 2010-05-20
I also got it working last night but I didn't do that. I did notice that that was happening. The hanging of the mysql server that is. 

I was reading some forums and came up with this solution This will wipe out all your mysql config and make you start from scratch...

If throughout this procedure anything hangs try to do the following...
sudo /etc/init.d/mysql stop 
 

sudo mv  /var/lib/mysql /home/oldvarlibmysql 

sudo dpkg --configure -a

sudo apt-get clean
sudo apt-get autoremove

I then had to stop the mysql with the following
sudo /etc/init.d/mysql stop  ( i think this is the real problem)

I then moved in to synaptic and deleted the mysql client , server, and common files 
There should be three packages but it might delete a bunch of other stuff. dont worry you can install it back later.

If it hangs while deleting try stopping mysql again I had to...

Now to be safe I rebooted since I finally got it unistalled.

Get back into synaptic and install the mysql-client, I think it automatically selects the server and common files. You might need to select the mysql-php also if it was removed. I had to do that...


Once it installs to be safe I rebooted again too be safe. I know you dont have to but it was so messed up I wanted to make sure It cleaned up well. 

Anyway good luck!

By the way if your synaptic gets stuck and you are forced to kill it, you can use the following to unlock it without having to reboot.

 sudo rm /var/lib/dpkg/lock

---

### Post by dgavenda on 2010-05-26
I've followed these steps and it still hangs on trying to start mysql.

root@dev-server:~# service mysql start


There's nothing in syslog or mysql log which makes this even more fun.

---

### Post by cmcginty on 2010-05-26
same here ... sometimes I just can't believe the stupidity of the bugs that are popping up in Ubuntu

is there a bug number for this yet? workaround?

---

### Post by maxideci on 2010-05-27
time is turning back...banging my head over mysql on lucid.

---

### Post by maxideci on 2010-05-27
> **cdcooper said:**
> I worked around this by editing the 
 /var/lib/dpkg/info/mysql-server-5.1.prerm
and
 /var/lib/dpkg/info/mysql-server-5.1.postinst
files, replacing the code to stop and start mysql (which seemed to be hanging):

	#stop mysql || :
	service mysql stop

and
	#start mysql || :
	service mysql start

It did not help me. in fact it even stalled apt-get -f autoremove.

---

### Post by cmcginty on 2010-05-27
[https://bugs.launchpad.net/ubuntu/lucid/+source/mysql-dfsg-5.1/+bug/551130](https://bugs.launchpad.net/ubuntu/lucid/+source/mysql-dfsg-5.1/+bug/551130)

I had success with the PPA link from post #15

---

### Post by maxideci on 2010-05-27
> **cmcginty said:**
> [https://bugs.launchpad.net/ubuntu/lucid/+source/mysql-dfsg-5.1/+bug/551130](https://bugs.launchpad.net/ubuntu/lucid/+source/mysql-dfsg-5.1/+bug/551130)

I had success with the PPA link from post #15

well installing from the above mentioned ppa gets stalled at 'Installing new version of config file /etc/init/mysql.conf ...'

---

