---
title: "Program to remove snap version of Firefox?"
date: 2022-11-19
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-11-19
Perhaps I made a mistake when I used the Yannubuntu boot repair program to recover Ubuntu Unity 22.04 on a dual-boot with Win 10 Pro, but when Ubuntu came back up, my non-span version of Firefox had been replaced by the snap version.  I went through the procedure given on kubntu forums to get the non-snap version back.  It would appear that someone could write a program that would carry the steps I did manually.  I am not an IT professional, so I will let others comment on the feasibility or lead me through writing whatever needs to be written.

Thank you,

John

---

### Post by ajgreeny on 2022-11-19
I need to know a great deal more about exactly what you did with boot-repair and if you used anything else, as there is no obvious way that I can think of that running boot-repair would add or remove any applications except for grub if that were necessary for a repair. I certainly can see no way that it would add back the snap version of firefox if you had removed it previously.

How did you actually remove firefox, and what are you now using in its place?

It is not too difficult to completely remove firefox, and if you wish to you can remove all other snap applications and the whole snap infrastructure as I have done. However, I will not waste time and space and tell you how to do so as there are many threads in this forum on that subject which should be easy to find.

---

### Post by mIk3_08 on 2022-11-20
> **cigtoxdoc said:**
> my non-span version of Firefox had been replaced by the snap version.  I went through the procedure given on kubntu forums to get the non-snap version back.  You can just always download the tar.bz compressed file of firefox. This will run to any kind of Ubuntu flavor. Regards and cheers.

---

### Post by ajgreeny on 2022-11-20
> **mIk3_08 said:**
> You can just always download the tar.bz compressed file of firefox. This will run to any kind of Ubuntu flavor. Regards and cheers.
Yes.
That's what I've been using since 22.04 "forced" snaps into the system.

It works brilliantly on all the distros where I've used it including Debian Unstable, where normally only the Firefox-ESR version is available, meaning I can use symbolic links to the same profile for all my firefox installations independent of the actual version of firefox.

---

### Post by oldfred on 2022-11-20
I prefer to use the ppa. It also updates my Thunderbird to latest version.
But you also have to change priorities or the snap gets reinstalled.

Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)


My first script was from my history file. I copied the commands, removed sudo as script is run with sudo. Added #!/bin/bash as first line, saved as xxx.sh and changed to executable. Good learning experience for first time script as not many commands to debug if it does not work.

---

### Post by mIk3_08 on 2022-11-21
> **ajgreeny said:**
> Yes.
That's what I've been using since 22.04 "forced" snaps into the system.

It works brilliantly on all the distros where I've used it including Debian Unstable, where normally only the Firefox-ESR version is available, meaning I can use symbolic links to the same profile for all my Firefox installations independent of the actual version of Firefox. I agree with it. I've been using this kind of Firefox for a while now. So far so smooth, good, fast and stable. In fact I am using this Firefox every time I open up ubuntuforums website. I haven't encountered any problem so far. Regards and cheers

---

