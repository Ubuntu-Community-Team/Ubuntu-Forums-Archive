---
title: "Installing Ubuntu 15 from USB"
date: 2015-06-12
forum: Installation &amp; Upgrades
---

### Post by gabmuks on 2015-06-12
Hello and good day to all.

I used Start up Disk Creator with a .iso file 
to make a USB start up disk. I used the .iso file
below to make the disk. But when I try to boot from
my USB, I get the message: "not a COM32R image."
That is all I get. Ubuntu does not load.
I have a 64-bit PC with the 64-bit version of Ubuntu 14 now.
And it is working great. SO why doesn't the Ubuntu 15 USB
start up? 

Thank you for your time.
[URL="http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/wily-desktop-amd64.iso"]wily-desktop-amd64.iso


[/URL]

---

### Post by sudodus on 2015-06-12
It is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801"). Try another tool to install Ubuntu, for example ***mkusb*** (or ***Unetbootin***, the version from the developer's PPA). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by gabmuks on 2015-06-12
> **sudodus said:**
> It is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801"). Try another tool to install Ubuntu, for example ***mkusb*** (or ***Unetbootin***, the version from the developer's PPA). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Thank you for kind reply.

I really wanted to use "mkusb", 

but the mskub instructions are too much for my level of knowledge.

I know how to get to terminal and copy and paste commands.

But the instructions are too confusing.

 I will try.

Thanks for your time.

---

### Post by sudodus on 2015-06-12
Well, I think you can install the PPA and mkusb.

 ```

sudo add-apt-repository universe       # in Ubuntu 14.04 LTS for pv
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

And then you select mkusb from unity's dash or type

```
sudo -H mkusb
```

in a terminal window. You might understand how to use it when you run it (and only refer to the manual or ask here, if you get stuck).

---

### Post by jhecn on 2015-06-12
From : [https://forum.ubuntu-fr.org/viewtopic.php?id=1705601](https://forum.ubuntu-fr.org/viewtopic.php?id=1705601) (in french).

When you see the error: "not a COM32R image"  enter "live". I have a USB stick like this and this works.

---

### Post by Geoffrey_Arndt on 2015-06-13
Pressing the "Tab" key should display a listing of live-boot options.    Usually the first or second entry (like "live32 or live64") will start the normal boot process (but on some live iso's the startup term is slightly different - - but try them all till you see which one works).

---

### Post by oygle on 2015-06-13
Thanks, I had exactly the same situation as the OP. Pressed TAB and entered **live**

---

### Post by gabmuks on 2015-06-13
Thank you all very much for your help.

I always appreciate your input.
I tried all the ways that are suggested including the mkusb method.
They all worked well up to the place in the installation process where they ask
if you want to download third party software. If I checked yes, the whole process would 
come to a halt. So after 3 tries, I stopped checking the yes box. Form then on,
everything worked great. I am up and running with Ubuntu 15 now.
Now I have to ask for help in another thread concerning browser speed.
It has really slowed down using Ubuntu. Compared to Windows 7, which
I have on the same computer, with the same browser, Ubuntu is at least ten times slower.
Ubuntu was never slower than Windows in the past.

Thanks much for your time.

---

### Post by sudodus on 2015-06-13
I think you have problems with the graphics driver, or maybe you would need more RAM for Ubuntu to run well. Please tell us about your graphics card/chip.

One alternative is to install a flavour of Ubuntu, that needs less CPU 'horsepower' than standard Ubuntu, ultra-light Lubuntu or medium light Xubuntu or Ubuntu Mate.

But with some luck you might find a good proprietary graphics driver and install it manually. The reason why it did not work with the third party software might be that it found and selected a bad driver automatically.

If the problems are not solved, I suggest that you stay with or re-install Ubuntu '14'. ***The version 14.04 has LTS*** (long time support until April 2019), but the following versions last only for 9 months after release. The next version with long time support will be 16.04 LTS (released in April 2016).

---

