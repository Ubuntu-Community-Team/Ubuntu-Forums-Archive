---
title: "ubuntu issues from grub, no large RAM, nvidia, freezes and no cc!"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by tariq on 2005-05-06
i finally plunged for ubuntu after years of mandrake. and the issues started:

[list=1]
[*]ubuntu won't boot off an xfs partition mounted as / - mandrake will

[*]i have 1.5Gb RAM - but ubuntu won't see it. mandrake will. i was told to use a different kernel - upgrading from 2.6.10 to 2.6.11 (using apt-get install) is fine, but now the nvidia X breaks. and dpkg-reconfgure or anything else like unintiall/reinstall of nvidia-glx doesn't work. the d*** nvidia-glx lists 2.6.10 as a specific dependency and wants to pull that in. grrr! i gave up and did it the old way - from nvidia.com/linux and that worked fine - so whats the point of apt-get and dpkg-reconfigure?

[*]more apt-get issues. ok i wanted to compile. no "cc". nvidia wanted to compile - again no "cc". i can't believe a base install doesn't have a c compiler. ok - so apt-get gcc and g++. seemed ok - but again "no cc". grrrr! so i was told apt-get install build-essential. it pulledin different versions of gcc and g++. again grrrr!

[*]old software - from old grub, old lyx, old firefox .. even with "universe" enabled. grrr! and that's just after one hour of using it.

[*]and worse of all! **Ubuntu freezes hard after about 5 minutes of use **now. i've seen posts about this but no clue as to solution - nothing strange in /var/log/messages. only a hard reset will restart the machine.
[/list] 

people have been helpful sure - but maybe ubuntu isn't for me?

---

### Post by shakin on 2005-05-06
[QUOTE=tariq]
[list]
[*]ubuntu won't boot off an xfs partition mounted as / - mandrake will
[/QUOTE]
Can't help you here because I don't use XFS. But then, does XFS really offer you more than ReiserFS? I'm not aware of a compelling reason to use XFS.

[QUOTE=tariq]
[*]i have 1.5Gb RAM - but ubuntu won't see it. mandrake will. i was told to use a different kernel - upgrading from 2.6.10 to 2.6.11 (using apt-get install) is fine, but now the nvidia X breaks. and dpkg-reconfgure or anything else like unintiall/reinstall of nvidia-glx doesn't work. the d*** nvidia-glx lists 2.6.10 as a specific dependency and wants to pull that in. grrr! i gave up and did it the old way - from nvidia.com/linux and that worked fine - so whats the point of apt-get and dpkg-reconfigure?
[/QUOTE]
First, you need the i686 kernel to enable bigmem. 2.6.11 isn't necessary and since I don't think it's even an official Ubuntu package, that's why it's causing you Nvidia problems.

[QUOTE=tariq]
[*]more apt-get issues. ok i wanted to compile. no "cc". nvidia wanted to compile - again no "cc". i can't believe a base install doesn't have a c compiler. ok - so apt-get gcc and g++. seemed ok - but again "no cc". grrrr! so i was told apt-get install build-essential. it pulledin different versions of gcc and g++. again grrrr!
[/QUOTE]
I don't know why build-essential isn't installed by default, but it could be for security. Hardened distros don't have compilers installed by default because using one would make it much easier for a user to elevate his permissions. There is also a chance that the reason why it's not installed is because it's not necessary for most people who only want to install software using Synaptic.

[QUOTE=tariq]
[*]old software - from old grub, old lyx, old firefox .. even with "universe" enabled. grrr! and that's just after one hour of using it.
[/QUOTE]
The official repository contains the distribution with security patches. It's not a rolling cycle of packages. Ubuntu Firefox 1.0.2 has several of the 1.0.3 security patches, but you may be interested in doing what everyone else is doing: enable the backports repositories. Backports have a rolling software cycle, which is what you want.

[QUOTE=tariq]
[*]and worse of all! **Ubuntu freezes hard after about 5 minutes of use **now. i've seen posts about this but no clue as to solution - nothing strange in /var/log/messages. only a hard reset will restart the machine.
[/list]
[/QUOTE]
Unfortunately I can't help you with this since I haven't had this issue. Did it start when you did your own kernel and nvidia driver? I suggest installing the i686 2.6.10 kernel and using the nvidia driver from the repository.

---

### Post by az on 2005-05-07
Basically, stick with a stock kernel (686 which will recognize all your ram) and that will fix many of your problems (2 and 5)

Ubuntu does not use XFS.  It can be compiled into the kernel, but ubuntu does not use it,  That's all.

Old software is relative.  You can always use Breezy, if you like.

---

### Post by TonioRoffo on 2006-07-12
Will the stock i686 kernel recognize >4gb RAM?

I want to use Ubuntu as a host for Vmware Server, but I don't have the "heavy hardware" yet so I'm not sure if it will work.

If not, what do I need to do?  Use bigmem?

Thanks for helping me out on this...

---

