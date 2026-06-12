---
title: "&quot;None Type&quot; object has no attribute 'get_info'"
date: 2014-12-06
forum: Installation &amp; Upgrades
---

### Post by odusseas on 2014-12-06
Hi !!
i am trying to install ubuntu without using CD or USB.
I have download ubuntu 14.04.1 LTS, and i take this error "None Type" object has no attribute 'get_info'       c:\user\hp\Appdata\local\temp\wubi-12.04rev266
i find some solutions like this :"[h=3]Known bug, please re-download the ISO and verify MD5 hash[/h][COLOR=#333333][FONT=UbuntuRegular]It appears this is a catch-all error usually thrown (shown) by [Wubi not recognizing or reading some piece of data in the ISO]("http://ubuntuforums.org/showthread.php?t=1641044") used for installation, which in turn is caused [by an error while downloading the ISO]("https://bugs.launchpad.net/wubi/+bug/989991").[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Please try [/FONT][/COLOR]*separately*[COLOR=#333333][FONT=UbuntuRegular] downloading the 12.04 i386 desktop ISO, and verify that the MD5 hash matches. Then launch Wubi and point it to the downloaded ISO.[/FONT][/COLOR]"

but i dont understand what i have to do...
from where i will download [COLOR=#333333][FONT=UbuntuRegular] 12.04 i386 desktop ISO, any link?
what iso i must verify?the new one?and how can do wubi point to downloaded iso?


i really need helppp :([/FONT][/COLOR]

---

### Post by ajgreeny on 2014-12-06
Wubi is dead so forget about that and do a proper partitioned installation of 14.04.1.

---

### Post by hakuna_matata on 2014-12-07
> I have download ubuntu **14.04.1** LTS, and i take this error "None Type"  object has no attribute 'get_info'        c:\user\hp\Appdata\local\temp\wubi-**12.04**rev266
I don't recommend Wubi because of poor support. Additionally, a Wubi for **12.04** doesn't work for **14.04.1**.

If you want install 14.04.1 with Wubi despite other recommendations, read this: [http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html](http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html)
> from where i will download [COLOR=#333333][FONT=UbuntuRegular] 12.04 i386 desktop ISO, any link?[/FONT][/COLOR]
If you still need this iso, here is a link to the download site: [http://releases.ubuntu.com/precise](http://releases.ubuntu.com/precise)

The iso for the latest point release 12.04.5 is: [ubuntu-12.04.5-desktop-i386.iso ]("http://releases.ubuntu.com/precise/ubuntu-12.04.5-desktop-i386.iso")

edit: Note that wubi-**12.04**rev[COLOR=#ff0000]266[/COLOR] is an old Wubi version for 12.04. It corresponds to [wubi-12.04.exe]("http://old-releases.ubuntu.com/releases/precise/wubi-12.04.exe") from the download site for old releases of 12.04:  [http://old-releases.ubuntu.com/releases/precise](http://old-releases.ubuntu.com/releases/precise)

---

