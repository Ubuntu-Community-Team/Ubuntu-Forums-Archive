---
title: "please help deleting personal details"
date: 2015-12-04
forum: Installation &amp; Upgrades
---

### Post by david471 on 2015-12-04
Hi Im selling a acer revo aspire.
It only has ubuntu as an operating system, but i want to delete all my personal info before selling

How do i do this ?
thank you in advance

---

### Post by SlidingHorn on 2015-12-04
If you're selling it, why not simply perform a clean install?  This would accomplish what you're looking for, and it would give the person you're selling the machine to a brand new environment with which they can change to their liking.

---

### Post by david471 on 2015-12-04
ok, how do i do that? im sorry im not great with computers....also i dont have a disc with ubuntu on

---

### Post by sudodus on 2015-12-04
Welcome to the Ubuntu Forums :-)

What version of Ubuntu are you running now? I suggest that you install the same version unless it has passed end of life. Test it with the following commands (in a terminal window)

```

lsb_release -a
# and
uname -a

```

and post the result in a reply.

---

### Post by david471 on 2015-12-04
12.04

x68_64

---

### Post by QIII on 2015-12-04
A reinstall will not remove the personal files from the machine.  It will only mark the physical areas of the disk where they are stored as free to be re-written.  The files themselves can be recovered.

If you want to really wipe it clean, I recommend DBAN.  "Nuke" the drive.

---

### Post by sudodus on 2015-12-04
***Edit:*** QIII is right about wiping / nuking the drive - if that is what you want.

-o-

Two versions of Ubuntu 12.04 LTS amd64 will be supported until April 2017, with the precise series of kernels, 3.2.0-xx, and the trusty series of kernels in 12.04.5 LTS, 3.13.0-xx.

You find this information from the command

```
uname -a
```

Download iso files from [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

You can boot a DVD disk or USB pendrive. Tell us if you need help to create a boot drive :-)

Get the 3.2.0-xx kernel from this iso file: [**ubuntu-12.04.1-desktop-amd64.iso**](http://old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-desktop-amd64.iso)

Get the 3.13.0-xx kernel from this iso file: **ubuntu-12.04.5-desktop-amd64.iso**

and bring it up to date with

```

sudo apt-get update
sudo apt-get dist-upgrade

```

and reboot

---

### Post by david471 on 2015-12-04
its 3.2.0-34

sorry is DBAN a command to use?

its running through the first command...

i dont know what get the kernel means though

tried the second but it says the package lists or status file could not be parsed or opened

if i can just know how to nuke it then i can be sure its clean, then i can stick an old windows disc on it or create a new ubuntu disc

---

### Post by sammiev on 2015-12-04
> **david471 said:**
> its 3.2.0-34

sorry is DBAN a command to use?

its running through the first command...

i dont know what get the kernel means though

tried the second but it says the package lists or status file could not be parsed or opened

if i can just know how to nuke it then i can be sure its clean, then i can stick an old windows disc on it or create a new ubuntu disc

Download it [here]("http://www.dban.org/") and make it bootable to a USB/DVD like you would with Ubuntu.

---

### Post by sudodus on 2015-12-04
> **david471 said:**
> its 3.2.0-34

The current kernel of that series is 3.2.0-95, so your installed system is very far from up to date.
> 
sorry is DBAN a command to use?
+1 to sammiev's advice> 
its running through the first command...

i dont know what get the kernel means though

tried the second but it says the package lists or status file could not be parsed or opened

if i can just know how to nuke it then i can be sure its clean, then i can stick an old windows disc on it or create a new ubuntu disc

For this kernel series you should download Ubuntu 12.04.**1** LTS amd64.

I checked but did not find it via the link in my previous post. Try this link instead: 

[ubuntu-12.04.1-desktop-amd64.iso](http://old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-desktop-amd64.iso)

with the following md5sum

```
06472ddf11382c8da1f32e9487435c3d *ubuntu-12.04.1-desktop-amd64.iso
```

You can see the whole directory at (when you scroll down)

[http://old-releases.ubuntu.com/releases/12.04.1](http://old-releases.ubuntu.com/releases/12.04.1)

---

### Post by david471 on 2015-12-04
ive just downloaded and saved to a usb, ubuntu 14
i put it in the revo and changed the boot menu to usb but it didnt work...

---

### Post by QIII on 2015-12-04
Did you download the iso file ***to*** the USB, save the iso to the USB from a download directory or did you create a live USB from the iso?

---

### Post by sammiev on 2015-12-04
There seems to be a problem writing the ISO to USB but there is a way.

You can also use the dd command to erase your HDD.

Check out this [thread]("http://ubuntuforums.org/archive/index.php/t-1701757.html") for the ISO and post #7 for the dd command method.

---

### Post by sudodus on 2015-12-05
> **david471 said:**
> ive just downloaded and saved to a usb, ubuntu 14
i put it in the revo and changed the boot menu to usb but it didnt work...

It might or might not work well with this newer version version of Ubuntu. Let us hope that it will work well :-) (I suggested to use the same version as you have now, to avoid the risk that there might be problems with some hardware drivers. I mean: why bother too much with a computer that you are selling?!)

-o-

Please check with [md5sum](https://help.ubuntu.com/community/UbuntuHashes) that the iso file was downloaded correctly.

You need a ***tool*** to 'install/clone/flash/burn/restore' the iso file to the USB drive. You cannot simply copy the file to the pendrive. See this link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by gordintoronto on 2015-12-05
The right approach is to use DBAN.

---

