---
title: "Running my linux partition in a Windows virtual environment"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by necropantser on 2011-10-06
Hey folks,

You know how Mac has Boot Camp and Parallels so that you have the option of booting to separate OS or using that same OS in a virtual environment?

Well, I want to do the same with my Windows and Linux partitions.  I have a licensed version of VMWare Workstation 7 for Windows, is there a way to do it with that?  If not, can it be done at all.

I love both my OS's, and I would like to be able to keep them both in place yet work with them at the same time if I feel like it.

Thanks for any advice!

---

### Post by lcman on 2011-10-06
Sure you can do that! First install windows and then install Vmware workstation on it. Open workstation and File > New > New virtual machine. Select install with blank drive to prevent vmware from using easy install. Before clicking on finish, click on customize hardware and go to the CD/DVD section. browse to your ubuntu linux iso image and select it. Click finish, boot the virtual machine and install ubuntu.

You can also check out the vmware workstation documentation, it's more detailed I think! :popcorn:

EDIT: You can also do that with Virtualbox though. That way, you can use Ubuntu as the host/main OS and windows as a virtual machine!

---

