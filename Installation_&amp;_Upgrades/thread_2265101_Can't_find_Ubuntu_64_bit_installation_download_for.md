---
title: "Can't find Ubuntu 64 bit installation download for USB"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by gabmuks on 2015-02-12
Does anyone have any info reguarding a 64 bit Ubuntu Installation
that I can download and install on a USB stick.

I'm not really sure how to ask this question.
 I want to install Ubuntu 14 on my 64 bit computer.
I wish to install Ubuntu to my computer from a USB stick.

I've already made a 32 bit Ubuntu USB installation stick.

Where can I find the 64 bit Ubuntu to make a USB installation stick?

I'm still not sure if I am asking this correctly.

---

### Post by SeijiSensei on 2015-02-12
Use the "amd64+mac" image from [http://cdimage.ubuntu.com/releases/14.04.1/release/](http://cdimage.ubuntu.com/releases/14.04.1/release/).

---

### Post by Penguin360 on 2015-02-12
> **gabmuks said:**
> Does anyone have any info reguarding a 64 bit Ubuntu Installation
that I can download and install on a USB stick.

I'm not really sure how to ask this question.
 I want to install Ubuntu 14 on my 64 bit computer.
I wish to install Ubuntu to my computer from a USB stick.

I've already made a 32 bit Ubuntu USB installation stick.

Where can I find the 64 bit Ubuntu to make a USB installation stick?

I'm still not sure if I am asking this correctly.

Go to [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop), then choose 64-bit from "Choose your flavour" drop down list, then click Download.

Is this what you are asking for?

[ATTACH=CONFIG]259938[/ATTACH]

---

### Post by gabmuks on 2015-02-12
> **SeijiSensei said:**
> Use the "amd64+mac" image from [http://cdimage.ubuntu.com/releases/14.04.1/release/](http://cdimage.ubuntu.com/releases/14.04.1/release/).

Thanks much for kind reply.

I have downloaded the image that you have recommended.

Do I have to "Extract" before I load to USB stick?

Was I supposed to download the image directly to USB stick?

Thanks for your time.

---

### Post by ajgreeny on 2015-02-12
> **SeijiSensei said:**
> Use the "amd64+mac" image from [http://cdimage.ubuntu.com/releases/14.04.1/release/](http://cdimage.ubuntu.com/releases/14.04.1/release/).

Unless you know something we don't, why did you suggest the **+mac** version for download? The OP doesn't mention using a mac.

---

### Post by gabmuks on 2015-02-12
> **Penguin360 said:**
> Go to [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop), then choose 64-bit from "Choose your flavour" drop down list, then click Download.

Is this what you are asking for?

[ATTACH=CONFIG]259938[/ATTACH]

Yes I guess that might be what I need.

But what do I do with the download?

Do I download directly to a USB stick?

Or do I have to download first to PC then transfer to USB stick?

I can't seem to find any instructions.

---

### Post by ubfan1 on 2015-02-12
You use a program like unetbootin or pendrivelinux on your Windows machine to put the iso image on the USB.  See [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)  and [https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

---

### Post by Penguin360 on 2015-02-12
> **gabmuks said:**
> Yes I guess that might be what I need.

But what do I do with the download?

Do I download directly to a USB stick?

Or do I have to download first to PC then transfer to USB stick?

I can't seem to find any instructions.

In your original post, you said you already made a 32 bit USB installation stick, then use the same software to make the 64 bit USB installation stick.

---

### Post by gabmuks on 2015-02-12
> **Penguin360 said:**
> In your original post, you said you already made a 32 bit USB installation stick, then use the same software to make the 64 bit USB installation stick.

Thank you for reply.

Yes earlier today, before I started this thread,I made my 32 bit USB stick from the PendriveLinux webside using Windows.

The PenDriveLinux Download said it was 32/64 bit. It did not give me a choice.

I then installed Ubuntu on my 64 bit PC from the USB stick. It seemed ok.

But if I look in Ubuntu where the OS is listed, it says that I have the 32 bit operating system installed.

The reason I am trying to get the 64 bit is because I still havent got my printer to work with the Ubuntu. (another thread of mine that is still open)

 One suggestion was that I download the correct Epson driver.   Which I tried.

 But Ubuntu software Center wont let me because it says the Epson driver is a 64 bit.

---

### Post by SeijiSensei on 2015-02-12
> **ajgreeny said:**
> Unless you know something we don't, why did you suggest the **+mac** version for download? The OP doesn't mention using a mac.

Because that's what that image is called.  Did you follow the link to cdimage.ubuntu.com?

OP, if you have an Ubuntu machine, it comes with a utility called "Startup Disk Creator." Use that.  Download the ISO, then point to it when you run the utility.

---

### Post by yancek on 2015-02-12
> The PenDriveLinux Download said it was 32/64 bit. It did not give me a choice.

Did you use the option 1 at the top of the pendrive window?  Use option 2, select your desktop iso by clicking on the Browse tab to the right and navigate to your Downloads folder or wherever you have the 64bit Ubuntu you want to use and then proceed.

---

### Post by gabmuks on 2015-02-12
> **SeijiSensei said:**
> Because that's what that image is called.  Did you follow the link to cdimage.ubuntu.com?

OP, if you have an Ubuntu machine, it comes with a utility called "Startup Disk Creator." Use that.  Download the ISO, then point to it when you run the utility.

Yes I can do that. But I have Ubuntu 32 bit installed.

If I use "Startup Disk Creator", will it make a 32 bit Ubuntu disk??

Thanks again for your help, but I am obviously not intelligent enough to figure this out

even with all the help. Guess I'll just use Windows for now.

I can mark this post "solved" if you want.

---

### Post by SeijiSensei on 2015-02-12
Not if you use a 64-bit Ubuntu ISO image.

---

### Post by ajgreeny on 2015-02-13
> **SeijiSensei said:**
> Because that's what that image is called.  Did you follow the link to cdimage.ubuntu.com?

OP, if you have an Ubuntu machine, it comes with a utility called "Startup Disk Creator." Use that.  Download the ISO, then point to it when you run the utility.
Yes, I did follow that link, but I say again, all those downloadable images are for **mac** or **powerpc** computers, which as far as I can make out is not what gabmuks is using.

I didn't want him to download an image, then spend time transferring it to USB, only to find that it will not work on his non-mac hardware, or am I missing something here, and the image files are now all named this way and work on both PCs and macs?

---

### Post by cl-netbox on 2015-02-13
Download link for LTS version ->
[http://releases.ubuntu.com/trusty/ubuntu-14.04-desktop-amd64.iso](http://releases.ubuntu.com/trusty/ubuntu-14.04-desktop-amd64.iso)
Download link for current version ->
[http://releases.ubuntu.com/utopic/ubuntu-14.10-desktop-amd64.iso](http://releases.ubuntu.com/utopic/ubuntu-14.10-desktop-amd64.iso)

Startup Disk Creator works only with the same version to install.
Better use the built in Disks application :
Insert USB device - open the application - choose USB device
Then click on the wheel and choose 'Restore Disk Image' ...

---

### Post by gabmuks on 2015-02-13
> **SeijiSensei said:**
> Because that's what that image is called.  Did you follow the link to cdimage.ubuntu.com?

OP, if you have an Ubuntu machine, it comes with a utility called "Startup Disk Creator." Use that.  Download the ISO, then point to it when you run the utility.

All of your instructions worked perfectly Sensei. Ubuntu 64bit and printer working great. Thanks to all of you for kind help and patience. I will mark this thread solved.

---

### Post by SeijiSensei on 2015-02-13
> **ajgreeny said:**
> Yes, I did follow that link, but I say again, all those downloadable images are for **mac** or **powerpc** computers, which as far as I can make out is not what gabmuks is using.
No, they are for "amd64+mac" meaning Intel-based Macintoshes.  The PowerPC builds are separate.  In fact, all the Ubuntu 14.04 builds for the PPC platform are the server version.  The desktop builds are all for Intel Macs.  I don't see any PPC desktop builds at [http://cdimage.ubuntu.com/releases/14.04.1/release/](http://cdimage.ubuntu.com/releases/14.04.1/release/).

---

### Post by ajgreeny on 2015-02-13
Thanks for that info [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/showthread.php?p=13227262#post13227262"), things have changed since I last downloaded an image file direct; I always use a torrent these days.

---

