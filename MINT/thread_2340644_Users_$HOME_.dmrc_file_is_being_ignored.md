---
title: "Users $HOME /.dmrc file is being ignored"
date: 2016-10-20
forum: MINT
---

### Post by borgward on 2016-10-20
Why is it being ignored?

The ownership and permissions appear to be correct:

-rw-------   1 tom tom          28 Oct  8 23:02 .dmrc I notice the date is 28 Oct. Today is 20 Oct. I had replaced mint 17 cinnamon with 18 cinnamon in / keeping my personal files in /home. could that date of 28 Oct from when I installed 17 be the problem?

---

### Post by Morbius1 on 2016-10-20
Just a guess but that error message lists two things that may be at fault. The .dmrc file and $HOME itself.

Your home directory should have permissions of:
> drwxr-xr-x
i.e., 755.

If it's 777 you will also get that error message.

Happens all the time when someone ignores the warning and creates a samba share of their home directory using Nautilus .. or in this case Nemo.

---

### Post by steeldriver on 2016-10-20
FYI 28 is the size of the file (in bytes) - the date is Oct 8

---

### Post by borgward on 2016-10-20
> **Morbius1 said:**
> Just a guess but that error message lists two things that may be at fault. The .dmrc file and $HOME itself.

Your home directory should have permissions of:

drwxr-xr-x 

i.e., 755.

tom@tom-Inspiron-1520120 ~ $ ls -la
total 14191736
drwxrwxrwx 126 tom tom       20480 Oct 20 12:23 . (777)
drwxr-xr-x   4 tom root       4096 Apr 12  2016 ..
...........................
-rw-------   1 tom tom          28 Oct  8 23:02 .dmrc


When I right click the home folder for the properties and look at the permissions tab I get 

[ATTACH=CONFIG]271695[/ATTACH]

> **Morbius1 said:**
> If it's 777 you will also get that error message. 

Happens all the time when someone ignores the warning and creates a samba share of their home directory using Nautilus .. or in this case Nemo.

So I need to change permissions for home to 755 and permissions for .dmrc to 644

---

### Post by Morbius1 on 2016-10-20
Well that's something you don't see every day. The output of "ls -la" doesn't match the "properties" in Nemo. Maybe that a new "feature" in Mint.

[COLOR=#0000cd]**EDIT**: Ah, that was Nemo properties for /home not /home/tom. Then it does match.[/COLOR]

I would change /home/tom to 755:
```
chmod 755 /home/tom
```
And leave .dmrc alone.

---

### Post by borgward on 2016-10-20
Right now .dmrc permissions are 600. Wonder why the message I get says to change it to 644?

---

### Post by Morbius1 on 2016-10-20
It really doesn't matter as long as it's not 664 or 666.

Mint deviates from Ubuntu on may things for unknown reasons ( at least to me ) and this is a Debian / Ubuntu error message that Mint inherits. In Debian / Ubuntu the default permissions are 644. In Mint it's 600.

---

### Post by borgward on 2016-10-20
Two other drives that have mint Cinnamon on them boot this laptop w/no error message when I install them on this laptop.

On a drive that has 17 cinnamon installed:

tom@tom-Inspiron-1520120 ~ $ ls -la
total 176
drwxr-xr-x 20 tom tom 4096 Oct 20 19:04 .
drwxr-xr-x 4 root root 4096 Apr 12 2016 ..

-rw------- 1 tom tom 29 Oct 20 19:04 .dmrc

New 1 TB drive that has install of 18

drwxr-xr-x 45 tom tom 12288 Oct 20 19:22 .
drwxr-xr-x 4 root root 4096 Oct 8 17:44 ..

-rw------- 1 tom tom 29 Oct 20 19:22 .dmrc

Both of the above drives ran in my laptop w/no error message at login

The drive that I am having trouble with:

tom@tom-Inspiron-1520120 ~ $ ls -la
total 14191748
drwxrwxrwx 126 tom tom 20480 Oct 20 19:37 .
drwxr-xr-x 4 tom root 4096 Apr 12 2016 ..

-rw-r--r-- 1 tom tom 32 Oct 20 18:01 .dmrc 

I want to change the permissions for this drive to match the other drives since they both boot in this laptop w/no error message at login.

I would do chmod 755 .  and  chmod 600 .dmrc Is that the correct way to change the permissions?

---

### Post by borgward on 2016-10-21
I changed the permissions for /home/tom to 755 and /home/tom/.dmrc to 600. No more error message at login page.

---

