---
title: "GRUB Questions/Issue - Please Help"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by Orius on 2007-11-19
Hello,
Recently installed Ubuntu 7.10 to my external usb hard drive along with GRUB. Windows XP Pro is installed on my internal hard disk. The issue/problem I am running into is that I get a GRUB error when booting the computer with the USB drive uplugged/turned off. GRUB gives Error 21 (Selected disk does not exist) which makes sense since the drive is off/not plugged. I cannot go any further after receiving the error.
My questions:
1) Is there no way to by pass this error and boot windows? Or is a "bypass/workaround" not possible because GRUB is installed on the unplugged/"missing" HD?
2) Would installing a GRUB partition on my internal HD (will always be there) allow me to by pass the grub error? How do I remove GRUB from Ubuntu on the external HD so that it will not conflict with the GRUB partition.
3) When I boot the computer with the USB HD unplugged/off where does the first part of GRUB boot from? Is there a portion of GRUB installed on the Internal HD (windows)? When looking at the windows drive I see no files or folders having to do with GRUB, so are the GRUB components stored in the MBR?

I have read over most of "[The GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm#21")" but have not found a good answer to my questions.

Thanks,
Zack

---

### Post by meierfra on 2007-11-20
Assuming that you are able to boot from the external hard drive, the following should  accomplish your goal:


Step 1:  Edit /boot/grub/menu.lst

Open a terminal (Applications->Accessories->Termimal) and type


```
cd /boot/grub   (This changes the current directory)
sudo cp menu.lst menu.lst.backup  (Creates a backup of the file  menu.lst)
gksudo gedit menu.lst     (Opens "menu.lst" in a new window)

```

In the file look for  

title ubuntu  kernel .......
root (hdx,y)  

Here x and y are some numbers. x should be 1, unless you have more than two hard drives.  If the ubuntu root partition is the first  partition on the second hard drive (hdx,y) will be (hd1,0), if its the third partition of the second hard drive it will be (hd1,2) (Grubs starts counting at 0). You need to remember the actual  values for x and y since we will have to use them frequently.

Replace all  

"root (hdx,y)"   in menu.lst by   "root (hd0,y)" 

 (So  for  example "root (hd1,2)  needs to be replaced by root (hd0,2)  )

You also need to replace

"#groot (hdx,y)" by "#groot (hd0,y)"

and 

title  Some Version of windows
root (hd0,z)   
makeactive
savedefault
chainloader +1

(z depends on the location of the windows partition on your internal hard drive. z is probably 0 or 1) 

by


title  Some Version of windows
root (hdx,z)
map (hdx) (hd0)
map (hd0) (hdx)
makeactive
savedefault
chainloader +1


Save the file and return to the terminal:

Step 2 Install Grub to the MBR of your external drive

```
sudo grub
```

this will give you a "grub>" prompt.

The next line is just to making sure that grub agrees with menu.lst on the location of the ubuntu partition:

```
 
find /boot/grub/menu.lst
```

It should  return (hdx,y)  with the exact same values for x and y as above. Type

```
root (hdx,y)

setup (hdx)

quit
```


Step 3  Reboot and set the Bios to boot from the external drive. Test whether you can boot into ubuntu and windows.



Step 4  Put Windows in charge of then MBR of the internal hard drive:

There are lots of ways to do this. Here is a method which  works from within a ubuntu terminal:

If you don't know the  ubuntu name for internal  drive (it should be /dev/sda or /dev/hday) you should be able to find it  by  typing "sudo fdisk -l"   in the terminal


```
sudo apt-get install ms-sys  (this installs  the program which will rewrite the MBR)

sudo ms-sys -m  /dev/sda 
```

Here in place of /dev/sda you need to use the actually name of the internal drive.

Unplug the external drive and you should boot directly  into windows.


If all those x, y and z are confusing you, just post the output of "sudo fdisk -l" and I'll rewrite the instructions.

---

