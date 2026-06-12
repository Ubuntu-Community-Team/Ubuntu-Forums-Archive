---
title: "How to allow file access during live boot? After failed upgrade to recover data"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by yangster on 2016-09-19
Hi guys,

I've failed to upgrade to 16.04 and now my system wont boot. I want to recover my data before I do a clean install.

I managed to do a liveboot using USB but I can't seem to access some files from my previous partition. Error msg is : "you do not have permission necessary to view the contents of..."

I tried
1) ```
sudo chmod -R ug+rw foldername
```(tried to allow read write access to the files through the root command line option in recovery mode and also in the liveUbuntu)
2) PressedAlt+F2, typed in sudo[gksu]("http://manpages.ubuntu.com/manpages/trusty/en/man1/gksu.1.html") nautilus  to the search bar within the live boot session entered but nothing happens. When i type [gksu]("http://manpages.ubuntu.com/manpages/trusty/en/man1/gksu.1.html") nautilus there wasn't even any response after enter.

Any suggestion?



Regards,
Yang

---

### Post by DuckHook on 2016-09-19
A LiveUSB uses special user ID: 999

Therefore, the command:```
sudo chmod -R ug+rw foldername
```…is not enough because your old _u_ser and _g_roup were likely 1000:1000 and 999 does not belong to any of them. You must allow at least read access to _o_thers as well:```
sudo chmod -R o+r foldername
```…or using octal (which I find easier):```
sudo chmod -R 664 foldername
```

Afterwards, you should be able to copy those files.

---

### Post by DuckHook on 2016-09-19
Also:
[LIST=1]
[*]pkexec is now the "official" way to run graphical apps as root,
[*]Therefore, gksudo has been deprecated,
[*]But apps need a policykit file in order to run pkexec,
[*]In the case of nautilus and gedit (Ubuntu devs decision), no policykit files are included
[*]Devs must feel that monkeying with files as root should be CLI-only (my conjecture)
[*]You can install policykit files for both nautilus and gedit with:```
sudo apt install nautilus-admin
```
[*]Or you can simply do:```
sudo -H nautilus
```The -H flag is critical, else you can really mess up some important config files and bork login.
[/LIST]

---

### Post by yangster on 2016-09-20
> **DuckHook said:**
> A LiveUSB uses special user ID: 999

Therefore, the command:```
sudo chmod -R ug+rw foldername
```&#8230;is not enough because your old _u_ser and _g_roup were likely 1000:1000 and 999 does not belong to any of them. You must allow at least read access to _o_thers as well:```
sudo chmod -R o+r foldername
```&#8230;or using octal (which I find easier):```
sudo chmod -R 664 foldername
```

Afterwards, you should be able to copy those files.


I tried using **sudo chmod -R 664 foldername **but somehow it prevented me from accessing my sub-folders and the sub-folder's logo turned to file-like.

Anyway I manage to fix the situation by using this instead [B]sudo chmod -R 755 foldername

[/B]Thank you for guiding though!

---

### Post by DuckHook on 2016-09-20
Odd. You shouldn't have to turn on the execute bit to allow reading and copying. But the important thing is that you have managed to back up.

I have also edited your post to take out the different fonts and styles in order to make it easier to read. When posting, please stay with standard formatting to keep the thread as easy to read as possible, especially for those using different devices (like mobile).

If your problem has been solved, *please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by Bucky Ball on 2016-09-20
Can't you just open a terminal and mount the partition then access folders as normal, or am I missing something?

Boot to Try Ubuntu> once at the desktop open a terminal> create a mount point> find device name of partition> mount it at mount point> open file manager and browse it. :-k

To find the partition name, e.g. /dev/sda4 or whatever:

```
sudo blkid
```

Create mountpoint:

```
sudo mkdir /mnt/data
```

Mount at mountpoint (with sda4 as example):

```
sudo mount /dev/sda4 /mnt/data
```

Open file manager and drill down to /mnt/data and you should see the data there. If you still have permission problems, open the file manager from a terminal as root and change permission of the folder/file:

```
gksudo nautilus
```

... then right click the file> properties> permissions.

---

### Post by yangster on 2016-09-20
@DuckHook well noted, will keep the format clean moving forward.

@BuckyBall Thanks for suggesting the alternative, may be useful for others. I've got it working already.

---

### Post by Bucky Ball on 2016-09-21
> **yangster said:**
> @BuckyBall Thanks for suggesting the alternative, may be useful for others. I've got it working already.

Ok. Then please mark the thread as solved to help others and save time. See link in my signature if you don't know how. Thanks.

---

