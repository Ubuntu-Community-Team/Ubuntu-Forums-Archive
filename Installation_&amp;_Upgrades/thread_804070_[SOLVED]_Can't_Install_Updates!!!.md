---
title: "[SOLVED] Can't Install Updates!!!"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by wok951 on 2008-05-22
I am fairly new to Ubuntu. I am trying to update and i have no clue what is going on. I keep getting an error message saying:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

E:_cache->open()failed,please report.

So if you can please help. Thank You

---

### Post by oilchangeguy on 2008-05-22
> **wok951 said:**
> I am fairly new to Ubuntu. I am trying to update and i have no clue what is going on. I keep getting an error message saying:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

E:_cache->open()failed,please report.

So if you can please help. Thank You

open the terminal (command line) and type sudo dpkg --configure -a

---

### Post by wok951 on 2008-05-22
Okay. I did that and this is what I got:

[sudo] password for (my username):

I try to put my password in but when i type it does not show up. Basically it won't let me type the password. And after 3 times it quites on me.

---

### Post by iaculallad on 2008-05-22
> **wok951 said:**
> Okay. I did that and this is what I got:

[sudo] password for (my username):

I try to put my password in but when i type it does not show up. Basically it won't let me type the password. And after 3 times it quites on me.

Linux does not show the password as you type in your terminal(but it's there). Just be very sure to enter the correct password corresponding to the correct username you used in the login screen.

---

### Post by abn91c on 2008-05-22
> **wok951 said:**
> Okay. I did that and this is what I got:

[sudo] password for (my username):

I try to put my password in but when i type it does not show up. Basically it won't let me type the password. And after 3 times it quites on me.

in linux you do not get ****** when you type a password in a terminal, just type it then hit enter

---

### Post by wok951 on 2008-05-22
Now I am getting something different when i type in sudo dpkg -configure -a.
I get:

dpkg: Unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


What now?

---

### Post by abn91c on 2008-05-22
[QUOTE=wok951;5022064]Now I am getting something different when i type in sudo dpkg -configure -a.

 type carefully it is:
 sudo dpkg --configure -a

---

### Post by wok951 on 2008-05-22
now after my password it gives me that same message

dpkg: Unknown option -o

Type dpkg --help for help about installing and deinstalling packages[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL)[*].

Options marked[*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by abn91c on 2008-05-22
> **wok951 said:**
> now after my password it gives me that same message

dpkg: Unknown option -o

Type dpkg --help for help about installing and deinstalling packages[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL)[*].

Options marked[*] produce a lot of output - pipe it through `less' or `more' !

you need to type 2 dashes before the word configure, the command is case sensitive or just copy and paste the one I typed earlier

---

### Post by wok951 on 2008-05-22
Okay. It sort of worked but now it just froze at this part:

Setting up capplets-data (1:2.20.1-0ubuntu1) ...


Does this take a while?

---

### Post by iaculallad on 2008-05-22
> **wok951 said:**
> Okay. It sort of worked but now it just froze at this part:

Setting up capplets-data (1:2.20.1-0ubuntu1) ...


Does this take a while?

Just take a bit of a moment. Be patient waiting.. once done, you're on the right track.

---

### Post by abn91c on 2008-05-22
update sometimes are slow, if you maximize the terminal window you can ussuall see a progress % at the bottom of the screen

---

### Post by wok951 on 2008-05-22
It worked but something popped up. The last little paragraph says:

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Errors were encountered while processing:
 libpng12-0

---

### Post by iaculallad on 2008-05-22
> **wok951 said:**
> It worked but something popped up. The last little paragraph says:

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Errors were encountered while processing:
 libpng12-0

Type this command on your terminal to resolve the problem:

**sudo apt-get install util-linux**

---

### Post by wok951 on 2008-05-22
IT WORKED!!! Thank you guys so much.

---

### Post by rotary12 on 2008-05-22
tnks to all,had same thing,just got here and its all ready solved:),tnks again

---

