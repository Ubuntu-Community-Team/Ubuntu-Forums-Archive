---
title: "not booted...give error black scree."
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by nitinpurohit111 on 2011-01-24
[I]ya i have ubuntu cd.
when i try to intall it inside the window through wubi intaller....i choose install inside the window.
after installing when computer reboots...i got two option. whrn i choose ubuntu for boot....
ifter 5-6 seconds a black screen appears like command...and intallation stopped here.{ this screen is full of lines....somthing like...Kvasprintf..//....
acpi,,??//

is says lots of about ACPI..... wht should i do..... when i boot through ubuntu cd...same problem arrives. i m new to ubuntu.}[/I]
Hi,

---

### Post by sikander3786 on 2011-01-24
Press any key as soon as the computer starts booting from the disc. You'll be present with a menu. Press F6 and select "acpi=off". Continue booting from the disc and you might see the desktop.

See here for details.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

As far as Wubi is concerned, you can edit the first line in Grub menu by highlighting it and pressing 'e'. Then navigate to the end of the line that says "quiet splash" and type "acpi=off" (without quotes) at the end. Press Ctrl + X to continue boot. If successful, you might need to make the change permanent.

But, I strongly recommend that if you intend to use Ubuntu for production purposes, a proper installation would be far better than Wubi.

Keep us posted ;-)

---

