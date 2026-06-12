---
title: "Install problem"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by MrGrado on 2011-08-03
I try to install, I get this:

[IMG]http://i592.photobucket.com/albums/tt8/gradosmack/error.jpg[/IMG]

---

### Post by Rubi1200 on 2011-08-05
Hi and welcome to the forums :-)

We need more information please to help troubleshoot this issue.

1. what version were you trying to install?

2. is this a Wubi or regular install?

3. please tell us what medium you are using; CD, USB stick etc.

Thanks.

---

### Post by MrGrado on 2011-08-07
I'm taking a different approach now. 

I have Ubuntu 11.04 running on a 100GB USB hard drive but not very well. I also have a 2GB USB thumb drive and a 2TB hard drive in my computer that is almost completely blank and I have another hard drive I can put into my computer too.

I want to put Kubuntu onto the 2GB USB so I can boot with that and then hopefully I have less problems because something real bad has happened to Ubuntu on the 100GB USB hard drive. 

I have two ISO files for Kubuntu. oneiric-alternate-i386(1).iso and oneiric-desktop-i386.iso

Alternatively I could install Kubuntu straight to the 2TB hard drive in my computer if it is going to be easy enough.

---

### Post by Karlchen on 2011-08-07
Hello, MrGrado.
> I have Ubuntu 11.04 running on a 100GB USB hard drive but not very well. [...]
I want to put Kubuntu onto the 2GB USB so I can boot with  that.All right. Let us start from here: You have got a running  Ubuntu system, even though it does not run well.
Your next target is putting Kubuntu on a 2 GB USB stick which you want  to use a bootable Kubuntu system (live system, installation medium, I  guess.)

As you did not tell whether you have got / need a 32-bit version or a 64-bit version of Kubuntu, we will simply assume 32-bit. The steps for  64-bit would be the same, only the ISO-file will have a slightly  different name.
As Oneiric is still under development, we will stick with Kubuntu 11.04  for the moment. The steps for Oneiric should be the same (or extremely  similar). Only the ISO-file will have a slightly different name. 

[LIST]
[*]Launch the existing Ubuntu 11.04 system.
[*]Get the current Kubuntu 11.04 ISO-image here: [**Download Kubuntu**]("http://www.kubuntu.org/getkubuntu/download#download-block")
Select to download "Kubuntu 11.04 32-bit"  and click the button "Begin download".
This should download the file "kubuntu-11.04-desktop-i386.iso", size: about 700 MB
[*]Save the file in the folder /home/<yourusername>/Downloads e.g.
[*]Attach the 2 GB USB stick to the machine
[*]Once the download has finished, launch **System** => **System Administration** => **USB Startup disk Creator**
[*]Inside the **USB Startup disk Creator**  select the downloaded ISO file "kubuntu-11.04-desktop-i386.iso" as the  source file and select the USB device as the target device.
[*]If  you would like to allow the future live system on the stick to remember  your settings between reboots, then activate the option to store  "settings and files in a reserved area"
[*]Click on the button "Create boot device".
Creating the bootable live system on the stick will take a few minutes.
[*]Once  **USB Startup disk Creator** has finished its job, you should give the newly created USB boot stick a try.
[*]Hopefully  your machine allows you to select the current boot device by pressing  F12 at boot time or by selecting the primary boot device inside the BIOS  setup.
[/LIST]
Provided your machine can be booted from the  newly  created Kubuntu USB boot stick, you can use this stick both as an  installation medium and install Kubuntu on a harddisk and as live system  without altering anything on the harddisks.

In case you experience any problems following the steps given above, do  not hesitate to tell so. Please, let us know what exactly you did and  which step did not work and which error message you received.

Good luck.
Karl

---

### Post by Karlchen on 2011-08-07
<content deleted, was duplicate of post above. where is the button to delete one's own post as long as there is no reply?>

---

### Post by MrGrado on 2011-08-07
Actually I managed to completely ruin my Ubuntu install before I read your post. I think my Ubuntu was too ruined to follow your instructions anyway. Now it gives an error message during booting about failing to mount something (s) to skip (m) to repair manually. If I choose manual repair I get a command line, If I skip I get into ubuntu but it will not connect to the internet anymore. 

So right now I am on a dinosaur windows machine making this post and putting Ubuntu onto my 2GB stick like I did originally to my 100GB USB HDD. I'm using Universal USB installer that I got from Pendrivelinux.com. I don't expect to have any problem with this part. It worked fine the first time I did it.

---

### Post by MrGrado on 2011-08-07
well thankyou Karlchen. I now have a USB drive with Ubuntu and another with Kubuntu.

---

