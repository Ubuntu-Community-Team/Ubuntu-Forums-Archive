---
title: "Installing ubuntu 14.04 fail"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by Comet220 on 2014-05-26
Never had Ubuntu before. Downloaded the 14.04 installer and ran it. Everything seemed fine but when I try and boot up my laptop with Ubuntu it comes up with:

[COLOR=#252525][FONT=Open Sans]serious errors were found while checking the disk drive for \[/FONT][/COLOR][COLOR=#252525][FONT=Open Sans]press I to ignore, S to skip mounting or M for manual recovery

Pressing I doesn't do anything, pressing M gets all kind of code **** I don't understand at all, and pressing S leads to:

the disk drive for /tmp is not ready yet or not present
press S to skip mounting, or M for manual recovery

If I press S again I can log in but then it's just a black screen with documentation **** or something and a line at the end that says something like: myname@ubuntu:~$

Help??[/FONT][/COLOR]

---

### Post by slickymaster on 2014-05-26
Hi Comet220, welcome to the forums.

That's a bug already reported on Launchpad. See [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792)

Please try the following when you get to _myname@ubuntu:~$_, which is your prompt in the terminal. Issue these commands one at a time:```
sudo mv /tmp /tmp_old
sudo mkdir /tmp
sudo chmod -R 777 /tmp
```Reboot your system and if you want you can delete the **/tmp_old** folder

---

### Post by Comet220 on 2014-05-26
Gave it a go. This is what happened:

myname@ubuntu:~$ sudo mv /tmp /tmp_old
unable to mkdir /var/lib/sudo/myname: no such file or directory
[sudo] password for myname:
mv: cannot move '/tmp' to '/tmp_old': Read-only file system
myname@ubuntu:~$ sudo mkdir /tmp
unable to mkdir /var/lib/sudo/myname: no such file or directory
[sudo] password for myname:
mkdir: cannot create directory '/tmp' already exists
myname@ubuntu:~$ sudo chmod -R 777 /tmp
chmod: changing permissions of '/tmp': Read-only file system
chmod: changing permissions of '/tmp/custom-packages': Read-only file system

Then I was back at square one. I hope this means something to you because I've got nothing.

---

### Post by slickymaster on 2014-05-26
Add explicitly the **/tmp** to the bottom of the file _fstab file_. Open your fstab file```
gksudo geany /etc/fstab
```and add the following to it```
tmpfs /tmp tmpfs defaults 0 0
```save the file and close it.
Afterwards run again the commands posted in post #2 and reboot.

---

### Post by Comet220 on 2014-05-26
Now I got:

myname@ubuntu:~$ gksudo geany /etc/fstab
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu
myname@ubuntu:~$ sudo apt-get install gksu
unable to mkdir /var/lib/sudo/myname: no such file out directory
password for myname:
W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to var/cache/apt
E: the package lists or status file could not be parsed or opened

Also I've never used command line or whatever you call this so when you tellmeto save and close a file, I don't know how to do that. Telling me exactly what to type is really helpful though.

---

### Post by slickymaster on 2014-05-27
The fact that your root filesystem (/) is being mounted as read-only could be that a disk error was detected on boot (errors=remount-ro option) or subsequent I/O error.

Can you please boot to with a liveCD and and run in a terminal window```
fsck
```to check your driver for errors. If **fsck** reports no errors and it is still read-only on reboot, you can run```
sudo mount / -o remount,rw
```to try to mount the disk read-write.

---

