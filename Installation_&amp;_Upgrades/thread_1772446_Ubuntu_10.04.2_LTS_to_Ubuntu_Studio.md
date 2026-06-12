---
title: "Ubuntu 10.04.2 LTS to Ubuntu Studio"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by 5h4dy on 2011-05-31
Hello, I am in need of some answers before I install the Ubuntu Studio desktop package. 

I am using an Acer Aspire One Zg5 which came with XP. I proceeded to install Ubuntu Netbook Remix. It then updated itself to 10.04.2 LTS I think. So everything is working perfect, but I want to install the Kernel-RT so I can do some producing in Ardour. What are the risks of converting inside Ubuntu? I'm afraid of being locked out of my computer...unable to use it. Also my netbook's monitor can only produce a 1024x600 Resolution, would converting to Ubuntu Studio Desktop force it to attempt to show 1024x768?

And what about hardware support?

---

### Post by snowpine on 2011-05-31
Installing the real-time kernel (linux-rt) is risk-free because you will still have the option to boot into your old kernel from the GRUB boot menu.

You don't need to install the entire Ubuntu Studio desktop if all you want is Ardour. Ardour is a stand-alone application that can easily be installed in "regular" Ubuntu. :)

---

### Post by 5h4dy on 2011-05-31
I do not have GRUB installed, and I'm using Ubuntu solely as my OS. Will installing the Ubuntu Studio Desktop package install GRUB so I can choose my kernels? 

Or would it simply convert my current Ubuntu into Ubuntu Studio?

Or does Ubuntu install Grub regardless, and not show it because I don't have a dual boot option?

---

### Post by snowpine on 2011-05-31
I think you have to press Shift or possibly Esc at boot-time to show the GRUB menu, but yes, you do have it installed (since your computer is able to boot). :)

As I mentioned above, ubuntustudio-desktop is not necessary to install ardour and linux-rt.

---

