---
title: "HELP! Main screen is GONE!"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by mastermarcus355 on 2008-09-14
OK so I had some problems with an installation error and I couldn't use my cursor. (The error was due to power manager) So I got to terminal, by using ctrl+alt+F1, and then uninstalled GNOME Power Manager thinking that I'd be able to use my cursor again and be able to reinstall power manager. But that didn't happen. Turns out now that I have a blank screen after logging in. I can still get to terminal but when I tried to reinstall it from there I had no luck. It wanted to grab the package from online repositories but said it couldn't get to the url's. So now I'm stuck and was wondering if there was a way to fix this or if I had to reinstall ubuntu? Either way I have no idea how to do either so any help is greatly appreciated! Thanks!

---

### Post by knattlhuber on 2008-09-14
The problem is likely not the missing gnome-power-manager but rather other packages that were uninstalled at the same time.

When I try to uninstall that package on my machine, Synaptic will also remove

*ubuntu-desktop* and
[I]gnome-session
[/I]
both of which are essential for the GUI to work. I guess that's what happened.

From the command line, please do

```
sudo dpkg --list | grep ubuntu-desktop
sudo dpkg --list | grep gnome-session

```

If the two packages don't show up in the list, please download them from [here]("http://packages.ubuntu.com/hardy/ubuntu-desktop") and [here]("http://packages.ubuntu.com/hardy/gnome-session"). Copy the files on an USB stick and we take it from there. The links assume that you are using 32-bit Hardy. If you use a different version, download the appropriate package from the same site.

---

### Post by mastermarcus355 on 2008-09-14
So I went to go try that and I don't have an option as to what OS I want to boot into!! Is there an alernate way to boot into ubuntu??

---

### Post by Sef on 2008-09-14
> So I went to go try that and I don't have an option as to what OS I want to boot into!! Is there an alernate way to boot into ubuntu??


From the terminal did you type in this command:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```?

If not, then try that.

---

### Post by knattlhuber on 2008-09-14
Sef, his network apparently isn't working if I understood his first post correctly. That's why I suggested to d/l the packages manually from the computer he's posting from. Or did I get that wrong, mastermarcus355?

---

### Post by mastermarcus355 on 2008-09-14
your correct knattlehuber...I did try and update and it said it couldn't retrieve the url's. So now I'm stuc...my original problem was I deleted the power manager and then the main screen was blank. So I went to go and type some commands into the terminal but I don't have an optin to boot into ubuntu. SO now I'm really stuck! lol Is there a way to get to terminal if not being able to boot into ubuntu?? Is there a way to get ubuntu as a boot option again??

---

### Post by mastermarcus355 on 2008-09-14
ohh...and Sef, I tried sudo apt-get update but didn't try sudo apt-get install ubuntu-desktop. I don't know if this matters or not.

---

### Post by knattlhuber on 2008-09-14
Your Ubuntu installation should still be working, it's just that your Gnome Desktop (the graphical user interface) is broken.
Now, when you boot your computer, you should end up seeing a command line prompt asking you to login. Is that correct?

---

### Post by mastermarcus355 on 2008-09-14
no I wish thats what happened...I have a dual boot setup with xp and now it doesn't give me ubuntu as an OS option. Before I lost ubuntu as an option to boot to, it would first go to the username screen(normal looking) and then the password screen(also normal looking) then it would go to the main desktop only it would stop short of displaying anything(had a blank peach colored screen). I could move the cursor around but had nothing to click on. I was able to choose ctrl+alt+F1 but now I'm not because I can't choose ubuntu as a boot option.

---

### Post by knattlhuber on 2008-09-14
Wow. OK. So we first need to fix your bootloader. Can you boot from the Ubuntu LiveCD, mount the Ubuntu partition from there and do

```
cat /yourHDmountpoint/boot/grub/menu.lst
```

where yourHDmountpoint is the mount point of your Ubuntu partition. It should start with '/media/...'

---

### Post by mastermarcus355 on 2008-09-14
OK so I restart my comp with the live cd in and then what do I choose?? and then once I get into ubuntu how do I mount the ubuntu partition and then how do I find the mount point of my ubuntu partition?? Sorry I'm still new..lol also I'm assuming that the code would be typed into terminal?

---

### Post by knattlhuber on 2008-09-14
Go to Applications > Accessories > Terminal and type

```
mount -t ext3
```

If your Ubuntu partition was automatically mounted, this will give you something like this:

```
/dev/sd... on /media/somefoldername type ext3
```

Now simply do

```
cat /media/somefoldername/boot/grub/menu.lst
```

and paste the output.


If your partition wasn't automatically mounted, do

```
sudo fdisk -l
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/devicename /media/ubuntu
```

You will get /dev/devicename of your Linux partition from your fdisk command output (the line that ends with 'Linux'). Once the drive is mounted, do as above (cat ... etc.)

---

### Post by mastermarcus355 on 2008-09-14
Thank you so much!...I will give this a try and hopefully I'll be able to boot back into ubuntu so I can get started on getting the GUI to work again! lol

---

