---
title: "Clean Installation"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2010-06-12
Hello guys!

Some time ago I've upgraded my Ubuntu to 10.04, but I didn't like it.
I'd like to do a clean install of previous 9.10 version, but I can't:(
I have image of 9.10 amd 64 on CD, but it can't see any partitions:/
[http://img203.imageshack.us/f/arghh.png/](http://img203.imageshack.us/f/arghh.png/)
Can anyone help me please?
I already removed old-linux partitions and created brand new ones (ext3 & linux-swap).
What should I do now?

Regards
Jet

P.S.
Do I need to add any Flags to new partitions?

---

### Post by dino99 on 2010-06-12
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oldfred on 2010-06-12
If you have partitions created in advance you use manual install and choose which partition is / (root) and what format to use ext3 or ext4 (or others), It seems to find swap without help. IF you have an existing /home you tell it to use it but not to format it.

---

### Post by jet-san on 2010-06-12
I it possible to use GParted instead of Parted Magic?

When I have my USB mounted - installation CAN see it.
[http://img508.imageshack.us/f/usbp.png/](http://img508.imageshack.us/f/usbp.png/)
but not my "normal" partitions:(

I'm unable to do "manual installation", cuz setup can't see my partitions:/

P.S.
After formatting my Linux's partitions I can't run my Win XP now.
How can I create new grub list?

---

### Post by oldfred on 2010-06-12
Do you still have a linux install or because you deleted the linux installs by repartiting the grub in the MBR has no place to go.

You can reinstall Ubuntu and it will put a new grub2 in the MBR and find windows. 

If you just want to boot windows for now you have to reinstall a windows boot loader to the MBR. Either from a windows repair CD run fixMBR or from Ubuntu liveCD.

Restore basic windows style boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

You only want the boot loader in the MBR so ignore any messages about the rest of lilo not being installed.

---

### Post by jet-san on 2010-06-12
I have the Ubuntu 9.10 CD and I'd love to install it, but I can't!
It doesn't recognise my partitions (either before and after format).
I even checked Parted Magic like someone suggested, but it's the same GParted there as here (Ubuntu LIVE session).
Still waiting for your help lads.

Regards
Jet

Btw: What's the difference between ext3 and ext4?

---

### Post by darkod on 2010-06-12
Except the upgrade to 10.04, which might have been from 8.04 too, did you ever manage to install 9.10 as clean install? Have you tried to check if you have raid metadata remains on the disk?

If the hdd was ever used in raid, it might have metadata remains and even formatting doesn't remove them. The symptom is that Gparted from live mode can see the disk, but the installer no.

In live mode, try this:

sudo dmraid -r -E /dev/sda (or depending what the disk name is)

If that asks to remove settings, and you are NOT running raid, remove them. See if the 10.04 installer will work (or 9.10).

---

### Post by jet-san on 2010-06-12
I did 2 clean Ubuntu installs in my life and both were 8.xx.
I did it twice, cuz I wanted to change 32bit for 64 version.
After that I did only upgrades (to 10.04 finally).
However I don't like new release.

I have no idea what are you talking about raid metadata, but I did what you said:P

```
ubuntu@ubuntu:~$ sudo dmraid -r -E /dev/sda
/dev/sda: "jmicron" and "isw" formats discovered (using isw)!
Do you really want to erase "isw" ondisk metadata on /dev/sda ? [y/n] :y
```

No, installer can't see it anyway:(

---

### Post by garvinrick4 on 2010-06-12
For some reason I have seen this same problem during install quite a few times this week.
#7 by darkod works it seems everytime.

---

### Post by garvinrick4 on 2010-06-12
```
sudo apt-get remove dmraid
```


Just go to try Ubuntu run this code and go to install.

Hope it works for you.

---

### Post by darkod on 2010-06-12
Usually the remove dmraid is not needed, but if it didn't work after removing the metadata, run that command as suggested too.

It did find metadata, so that should have been the problem. Even after restart it doesn't work? You don't have any raid setting enabled in BIOS by mistake do you? Because it might put settings back on the disk again as soon as you remove them.

---

### Post by jet-san on 2010-06-12
> **garvinrick4 said:**
> ```
sudo apt-get remove dmraid
```
Just go to try Ubuntu run this code and go to install.

Hope it works for you.

Omg!
[http://img266.imageshack.us/i/luv.png/](http://img266.imageshack.us/i/luv.png/)
I luv ya mate!

Thanks a lot:)
jet

---

### Post by garvinrick4 on 2010-06-12
> **jet-san said:**
> Omg!
[http://img266.imageshack.us/i/luv.png/](http://img266.imageshack.us/i/luv.png/)
I luv ya mate!

Thanks a lot:)
jet

You are welcome mate, mark as solved if you would.

---

### Post by jet-san on 2010-06-13
Marked as SOLVED.

Big thanks to all of you guys for help!

---

