---
title: "the way of ubuntu installation seems to be wrong."
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by baryonicdm on 2013-11-20
i downloaded ubuntu server and desktop on ubuntu download page. 
and on my virtualbox, i`ve installed each of ubuntu but.. 

i found out that i should wait for many downloads that i don`t know what that is. 
furthermore, network seems to be very slow. 

is there another way that i can install ubuntu without downloading files ? 
i`ve removed check sign on radio checkbox for install updates. 

if there is no other option, then it seems to be very wrong. 


i know that ubuntu is becoming something great 
but so much waiting for installing ubuntu. 


sorry for my bad english.

---

### Post by buzzingrobot on 2013-11-20
The Ubuntu installer allows you to avoid downloading updates during the initial installation.  You appear to have done that.  Other packages may also be pulled in over the net, including proprietary codecs, etc., if you choose that installation option.

If you wish to install updates and security patches, you will need to download them at some point, of course.

Ubuntu has no control over the speed and bandwidth of the local net connection.  It is safe to say, though, that the software distribution schemes used by Ubuntu and all other modern Linux distributions implicitly assume the user has access to a fast high-bandwidth connection that can handle many megabytes of traffic in minutes, rather than hours.

An option for you may be to explore using the minimal ISO approach to installing Ubuntu.  This initially installs only the most minimally necessary packages, allowing the user to add only the specific packages of interest.

---

### Post by coffeecat on 2013-11-20
> **baryonicdm said:**
> is there another way that i can install ubuntu without downloading files ? 
i`ve removed check sign on radio checkbox for install updates. 

If you've unchecked the radio button, then it won't download updates and you can update the system after you have installed it.

What may have been causing a delay is that it will download language packs even if you've unchecked the update button. According to [this askubuntu page]("http://askubuntu.com/questions/166063/ubuntu-installation-issue"), there is a skip button to skip that step, although I must admit I've never noticed it. Alternatively, the easiest way to avoid download delays if you have a slow connection is to simply disconnect the live session from the internet before you start the installer. An installation with no downloads takes no more than twenty minutes in my experience.

---

### Post by grahammechanical on 2013-11-20
I have experimented installing Ubuntu in a VM and I have learned that my machine does not have the power to run VMs satisfactory. So, your hardware will affect performance.

It is more usual to install Ubuntu to the hard disk. What we are installing is an image of Ubuntu that was fixed at the date of release. So, in the mean time things have been updated but it is up to you if you wish to upgrade your system.

You need to understand that Linux distributions are not developed in the same way as operating systems that are produced for sale. Linux is under constant development. Imagine installing windows XP and over the years through weekly or monthly updates it becomes Windows 8. Yes, you would have to do lots of updates to get to that situation. Well, it is like that with Ubuntu. I have gone from Ubuntu released in April 2007 to Ubuntu released in October 2013 by doing regular updates and a six monthly upgrade. I am putting it simply to show the difference between installing Ubuntu and buying what you think is a finished operating system but which then need Service Pack 1 and Service Pack 2. Or even to buy a new machine to run the latest OS.

And do not forget that we get ubuntu without charge. No one is forcing us to use Ubuntu. If we do not like the way things are done we can always uninstall Ubuntu. And in a VM that is very easy.

Regards.

---

### Post by ibjsb4 on 2013-11-20
> **coffeecat said:**
> If you've unchecked the radio button, then it won't download updates and you can update the system after you have installed it.

What may have been causing a delay is that it will download language packs even if you've unchecked the update button. According to [this askubuntu page]("http://askubuntu.com/questions/166063/ubuntu-installation-issue"), there is a skip button to skip that step, although I must admit I've never noticed it. Alternatively, the easiest way to avoid download delays if you have a slow connection is to simply disconnect the live session from the internet before you start the installer. An installation with no downloads takes no more than twenty minutes in my experience.

I have not tried this either, but I do know (like graham said), loading a VM on slower equipment (in my case a dual core @2.4Ghz) is a slow process.  I usually get to a point in the install that I get a blank screen that can last anywhere from 10 minutes to 30.  Depends what I am up to.

---

### Post by coffeecat on 2013-11-20
> **ibjsb4 said:**
> I have not tried this either, but I do know (like graham said), loading a VM on slower equipment (in my case a dual core @2.4Ghz) is a slow process.  I usually get to a point in the install that I get a blank screen that can last anywhere from 10 minutes to 30.  Depends what I am up to.

Yes, agreed, an installation in a virtual machine on a slower machine would take longer than I said. I originally read the OP's post as saying that they had installed desktop and server versions, **and** installed Ubuntu into a VM, but on re-reading the post I think I may have got that wrong. Perhaps they are saying they tried each of server and desktop only in a VM, which would be slower. However, they do seem to be saying that the download bit is the main delay.

---

### Post by baryonicdm on 2013-11-20
thanks guys. 

i`ll try skip button. 

by the way, my laptop is i7, ram that is allocated to vm is 6GB
network is also gigalan.

---

### Post by buzzingrobot on 2013-11-21
> **baryonicdm said:**
> i downloaded ubuntu server and desktop on ubuntu download page. 
...
i found out that i should wait for many downloads...


If you are installing something older than the current 13.10 release -- say, the 12.04.03 LTS -- there will be a considerable number of packages downloaded on the first update.

---

