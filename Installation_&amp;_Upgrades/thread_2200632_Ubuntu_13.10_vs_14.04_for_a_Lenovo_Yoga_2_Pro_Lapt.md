---
title: "Ubuntu 13.10 vs 14.04 for a Lenovo Yoga 2 Pro Laptop?"
date: 2014-01-20
forum: Installation &amp; Upgrades
---

### Post by haziz on 2014-01-20
[FONT=Menlo]I just picked up a [Lenovo Yoga 2 Pro]("http://shop.lenovo.com/us/en/laptops/ideapad/yoga/yoga-2-pro/") laptop today and want to install Ubuntu on it. I intend to dual boot for the moment with Windows 8.1 and will try to maintain the secure boot setup. As some of you probably already know the laptop is cutting edge with features such as a 3200 x 1800 screen resolution, backlit and touchscreen, and a "laptop to tablet folding behavior" [/FONT][FONT=Menlo]which has created an endless number of issues for early adopters wishing to install Ubuntu or other Linux distros on it. [/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]I normally never install alpha software on a machine but was thinking about it on this machine since the newer kernel and modules may allow better handling of cutting edge hardware. I realize that I will be installing alpha software and will avoid doing any mission critical work on the machine. I will also maintain a separate home partition in case I need to downgrade the install or rescue user data.[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]So 14.04 or 13.10 for this machine?[/FONT]

---

### Post by grahammechanical on 2014-01-20
You will be interested in this blog post by Stephen Webb who seems to know what he is talking about.

[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)

I think that the problem he is discussing will be there whether you install 13.10 of 14.04. Me, I have a fairly standard desktop and I have been using 14.04 since the start of the development cycle. It is stable enough to be boring. One little bug still remains.

The login password field will not accept any typed characters until after I have double clicked an app indicator icon (such as the keyboard indicator). It is an intemitent fault that may not be there is a fresh install from the latest image. Other than that I would say that as you are aware of the risks and have taken precautions then  install Trusty Tahr. You will get any improvements that will come into 14.04 including ( may be) a solution to the pixel size problem. I do not think that such solutions will be back ported to 13.10 because of the short support life of 13.10.

Regards.

---

### Post by oldfred on 2014-01-20
You can always install both. :)

With new drives you should have plenty of room as you only need about 20GB for / (root). I prefer smaller system partitions and larger data partitions even for Windows.

I do not attempt to share /home across installs, but have data partitions (both NTFS & Linux) and link common data back in. Then my /home is only about 2GB with most of that .wine. So I leave /home in my / and may copy some settings from one to another but not many normally.

---

### Post by bregma2 on 2014-01-20
Use 14.04 because it has the newer kernel, which has critical fixes for some video driver problems that can cause blackscreen.  You will probably still have wireless connection problems, if so the solution is "sudo echo 'blacklist ideapad_laptop' >> /etc/modprobe.d/blacklist.conf" from a terminal to blacklist a broken driver.

14.04 is stable enough for most daily usage.

---

