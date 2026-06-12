---
title: "Video driver won't load unless I launch &quot;Recovery Menu&quot; first???"
date: 2018-10-04
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2018-10-04
Help. I don't know why, but suddenly Ubuntu (64bit 18.04.01 LTS) won't start without going through the Recovery Mode menu first. I don't have to check or change anything. Just click "Resume" to finish the boot process. ] (*,)

The other day I had to manually d/l & reinstall the nVidia graphics driver. Now, every time I start Ubu, The only way I can get back into the normal Ubu desktop is to select "Recovery Mode" first from the GRUB boot menu, and once the text menu appears, select "resume", which finishes the normal boot and everything is fine (including graphics driver.)

If I simply select "Ubuntu" from Grub, startup switches resolutions a few times, a brief horizontal bar of garbage, then I lose my video signal and my monitor shuts off. :confused:

In Recovery Mode, I try "fix dpkg" but it says it can't connect (I'm connected.) When I do get to the desktop, I run the "Software Updater" and it reports:

"Failed to Download Repository":
[IMG]https://www120.zippyshare.com/i/0nh8wTVR/49838/Failed%20to%20dl%20repos.png[/IMG]
...my Internet connection is fine.

I click OK, and it proceeds to download & install my updates. I don't know which "Repository" it can't connect to in order to remove it.
And is the the updated video driver (downloaded from nvidia's own website) the reason Ubu won't start normally anymore? The system won't allow me to go back to the old method:
[IMG]https://www61.zippyshare.com/i/kqd1pG7t/4045/Can%27t%20set%20Update%20to%20update%20driver.png[/IMG]

This is all very annoying. How do I fix this? TIA

---

### Post by Bashing-om on 2018-10-05
Mugsy323' Yukkie -

Nvidia themselves advise do not do that .
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.


so now we got to see what it takes to remove the OEM driver;
what shows:
```

sudo find / -name "NVIDIA-Linux-*"
dpkg -l | grep -i nvidia
lsmod | grep nvidia
dkms status

```

Then we want to know the card we are installing the driver for:
```

lspci -k|grep -iEA5 'vga|3d'

```
to verify the driver to be installed.

[INDENT][INDENT]nothing but a thing ?
[/INDENT][/INDENT]

---

### Post by Mugsy323 on 2018-10-05
> **Bashing-om said:**
> Nvidia themselves advise do not do that.

Live & Learn.

Thanks for the reply. :D

> **Bashing-om said:**
> 
so now we got to see what it takes to remove the OEM driver;
what shows:
```

sudo find / -name "NVIDIA-Linux-*"
```

Here is what I get executing that first command:

```
find: ‘/run/user/1000/gvfs’: Permission denied
/home/mugsy/Downloads/NVIDIA-Linux-x86_64-390.87.run
find: ‘/proc/2586/task/2586/net’: Invalid argument
find: ‘/proc/2586/net’: Invalid argument
```

Gack! :o

---

### Post by Bashing-om on 2018-10-05
Mugsy323; Well ,,

not much given to work with , working with what we have,
The run file also contains a UN-installer.
```

cd /home/mugsy/Downloads/
sudo NVIDIA-Linux-x86_64-390.87.run --uninstall

```

[INDENT][INDENT]try'n 2 help
[/INDENT][/INDENT]

---

### Post by Mugsy323 on 2018-10-06
> **Bashing-om said:**
> not much given to work with , working with what we have,

:p

Yeah, I saw that coming. I'll let you know. Thanks.

---

### Post by Mugsy323 on 2018-10-07
> **Bashing-om said:**
> Mugsy323; Well ,,

not much given to work with , working with what we have,
The run file also contains a UN-installer.
```

cd /home/mugsy/Downloads/
sudo NVIDIA-Linux-x86_64-390.87.run --uninstall

```

Sorry for the late reply. Busy weekend. A/C out. :(

When I try the above command, I get:

*sudo: NVIDIA-Linux-x86_64-390.87.run: command not found*

I tried "chmod +x NVIDIA-Linux-x86_64-390.87.run" and trying again, but it made no difference. :eek:

---

### Post by Bashing-om on 2018-10-07
Mugsy323; Hummm ...

"find" said:
> 
/home/mugsy/Downloads/NVIDIA-Linux-x86_64-390.87.run

what now shows:
```

ls -al /home/mugsy/Downloads/NVIDIA-Linux-x86_64-390.87.run

```
Maybe we got to explicitly declare where the file is.
" ./Nvidiawhatever.run --uninstall" ??

[INDENT][INDENT]maybe ?[/INDENT][/INDENT]

---

### Post by Mugsy323 on 2018-10-07
Thx. A little searching online, I found:

*sudo nvidia-uninstall*

nVidia's own uninstaller did the trick. I then rebooted and reinstalled the driver "properly" using the "Software & Updates" utility (just search "driver".)

Not only did it properly install the latest driver, but Vulkan too, and booting is back to normal! Yea!

Thanks.

PS: You were probably right about needing the "./" prefix.

---

### Post by Bashing-om on 2018-10-07
Mugsy323; Outstanding :)

Pleased ya got it fingered out .

If this matter is concluded to your satisfaction ->
 Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]and we have more fun else-when
[/INDENT]

---

