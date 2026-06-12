---
title: "UBS external HDD not recognised!"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by jbh911 on 2012-03-17
I'm running Ubuntu 10.04 and yesterday ran updates which included Linux 2.6.32-39-generic. Following the successful installations of the updates I removed the 3 older kernel versions to reduce the size of the Grub boot page.
I then went to image my HDD using Clonzilla, which has been a routine for some years, but my USB external HDD was not recognised. Many attempts were made but to no avail.
The only USB item I could get my PC to recognise is a 4GB imitation memory stick, but it's recognised as usb0 and with the HDD icon appearing on the screen and in the Places directory. There was also a Rubbish Bin appearing in Places after I'd accessed usb0 - with 2 items which exist on the POCKET memory stick!
When I attempted to unmount usb0, a popup screen asked: Do you want to empty the rubbish bin before you unmount? The response to both Yes & No was: Unable to unmount: /media/usb0 is not in the fstab (and you are not root ).
The usb 4Gb memory stick is known as POCKET and appears in Places as the usual memory stick icon and with POCKET as its name, but is not accessable.

What do I need to do to get my USB external HDD recognised  by my PC?

This is the first issue I've had with 10.04, its just kept on keeping on.

:p

---

### Post by coffeecat on 2012-04-08
@jbh11, I've only just come across this post, and you haven't logged in for a couple of weeks, but I hope you see my reply.

> **jbh911 said:**
> 
When I attempted to unmount usb0, a popup screen asked: Do you want to empty the rubbish bin before you unmount? The response to both Yes & No was: Unable to unmount: /media/usb0 is not in the fstab (and you are not root ).

That sounds as if you have installed the application usbmount which is intended only for GUI-less systems. It interferes with the automounting functionality of the GUI desktop.

> **jbh911 said:**
> What do I need to do to get my USB external HDD recognised  by my PC?

If you are running a GUI desktop, and not the server version of Ubuntu, uninstall usbmount.

---

