---
title: "Installation keeps on freezing"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by xieem on 2017-07-24
Hi guys,

first I'll post a hardware spec of my pc than I'll describe the problem:

mobo: Asus 710I Pro Gaming
CPU: i7-6700k Skylake
RAM: 2x8gb HyperX Kingston
SSD: M.2 Samsung 850 EVO
GPU: Asus STRIX-GTX960-DC2OC-4GD5

So, I wanted to install Ubuntu Desktop "ubuntu-17.04-desktop-amd64" on this setup. 

But it's not working out as it should be, every time I want to start the installation the installer reboots or freezes after 2-3 minutes in the installation environment. Only a reboot makes the pc active again.

I literally have no idea what I do wrong, I use a Sandisk USB stick to boot over USB.

Any solutions would be greatly appreciated.

Kind regards

---

### Post by xieem on 2017-07-24
Now it even doesn't want to go to the installer, it just reboots after selecting install ubuntu

---

### Post by Bashing-om on 2017-07-24
xieem; Hello - Welcome to ubuntu .

First order of operations is to get that installer booting .
Now one has to :
A) verify that the .iso that you downloaded is consistent :
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
B) Verify the copy to the USB device is good:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
C) If you boot to a black/degraded GUI then apply a boot option - nomodeset ?? -
   "A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a black screen or show corrupted splash screen. See : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter" .

Once we have that installer booting and verified all works as expected in this environment, then install ubuntu .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by BenginM on 2017-07-24
Salutations! and welcome to the forums .

first i'd follow Bashing-om , looking at the specs .. the machine has a hybrid graphics. As the CPU: i7-6700k Skylake  has an Intel Integrated built-in Integrated Intel® HD Graphics and a discrete graphic NVIDIA GeForce GTX 960 , am sure if you disable the Nvidia GPU in the BIOS the installer will carry on , it seems as the GeForce is not excepting the the free nvidia driver Nouveau which is loaded and set by default in the kernel , and trying to reach the proprietary Nvidia driver which is not installed by default , one must install the proper driver version for the GTX form the additional driver section , or select it manually by running  the following in a terminal shell :
ubuntu-drivers devices 

Wait at least one minute for the command to scan your computer and 
generate the list of drivers. The output of this command will be a list 
of the package names and short descriptions of the available drivers. In
 addition to showing a list of the available drivers, the above command 
will often also identify the recommended proprietary driver(s) for your 
system.
 Install the recommended proprietary NVIDIA driver. If the name of the  recommended proprietary NVIDIA driver is, for example,  "nvidia-example-driver" install it using the following:


  sudo apt install nvidia-example-driver # replace nvidia-example-driver with the name of the recommended driver  sudo reboota

at this point you'll need to disable the built-in Intel GPU from the BIOS.
or if the installer is failing for some reason. in that case i would suggest you try using the mini iso to install .. it's fairly simple, Make sure you're connected through wired ethernet connection. and when you get to the software selection section hightlight the desktop environments software package you want , for Ubuntu Unity i think it's ubuntu-desktop , for lubuntu it's lubuntu-desktop, and so on. #see:

[https://www.youtube.com/watch?v=U42Ln3k7VK0&t=540s](https://www.youtube.com/watch?v=U42Ln3k7VK0&t=540s)

[URL="https://www.youtube.com/watch?v=fIfQ8SehcNU"]https://www.youtube.com/watch?v=fIfQ8SehcNU

[/URL][URL="https://help.ubuntu.com/community/Installation/MinimalCD"]https://help.ubuntu.com/community/Installation/MinimalCD


[/URL]

---

### Post by xieem on 2017-07-25
Hi guys,

thanks for the reply, I removed the GFX card and I am now using the on board gfx card. Still the same issue, the installer is freezing up. I'll do the verification checks as we speak and keep you posted, might give it a shot with ubuntu-16.04.2-desktop-amd64

---

### Post by xieem on 2017-07-25
Ok guys,

I got the installer up & running, now it freezes when I have to select the keyboard layout, literally starting to run out of options

---

### Post by xieem on 2017-07-25
Ok, when I deselected updates through installation I could go to where you have to fill in pc details, there I received an installer crashed.  [IMG]https://www.dropbox.com/s/4zdig3mcc2gxiyj/IMG_2677.JPG.jpeg?dl=0[/IMG] I added screenshot and it looks like it is thinking the USB is a harddrive. Hmm

---

### Post by BenginM on 2017-07-25
Set the boot option order in the BIOS to boot from the usb. and try again ..!

---

### Post by xieem on 2017-07-25
@bengin the boot order is booting from USB first

---

### Post by BenginM on 2017-07-25
Ok, please sha256 checksum the hashes of the iso you ,  use a 64-bit iso as the system CPU is a native Intel 64 . so download  this iso image and verify it's hashes 
[64-bit PC (AMD64) desktop image]("http://releases.ubuntu.com/xenial/ubuntu-16.04.2-desktop-amd64.iso") 

checksum hashes with either md5 or SHA256SUMS , see how to here :
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
these hashes file are in the same download page , scroll down :
[http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/)

Also , what is the OS you''re using to burn the iso to usb , i presume it's MS Windows if so , use Unetbootin or Rufus *USB* installerl  , i found dding the iso to usb has the best usb bootable result .

---

### Post by xieem on 2017-07-25
Hey BenginM , I use Mac OS Sierra so I use Unetbootin, perhaps an alternative?

---

### Post by BenginM on 2017-07-25
Hiya xieem , cool , an alternative method would be dd .. but lets first try booting the live usb with the kernel parameter nomodeset.. when you boot from the usb you see a screen like this:

[ATTACH=CONFIG]276135[/ATTACH]

press TAB , and you'll see another screen where you can add nomodeset , like so

[ATTACH=CONFIG]276135[/ATTACH]

after addin it press enter to boot with it

---

