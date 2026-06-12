---
title: "Windows 8 does not appear on GRUB2 and refuses to boot anyway!"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by epixpivotmaster on 2013-03-30
Hello everyone! My first post here, so yay! Great community you guys have here, congratulations! Loving Ubuntu by now!

But my problem is **much** more complex than the thead title sugests. Sitck with me for a sec...
Here's my current HDD setup (got only one):

[IMG]http://s14.postimg.org/a6q3yplwx/asas.png[/IMG]

When I turn on my pc, GRUB only shows my Ubuntu 12.04 x64 (and other variants, like Ubuntu's memory recover). No Windows 8 Ultimate x64 (/dev/sda2) to boot up.

The cause of this is known: I had Windows 7 Ultimate x64 on /dev/sda1, Windows Stuff (which has no OS, just lots of large files and programs like Steam, Adobe CS6 Master Collection, Fraps recordings, etc.) on /dev/sda2, Windows 8 Ultimate x64 on /dev/sda3, and Ubuntu 11.04 x64 on /dev/sda5. The installation order was: Windows 7 > Ubuntu 11.04 > Windows 8. After the last instalation, only Windows 8 and Windows 7 showed up on the booting screen (there was no GRUB). I used my PC like that for about six months. Then I wanted to delete Windows 7's partition completly (wasn't using it anymore, Windows 8 was much faster) and install Ubuntu 12.04 (I didn't know I could install GRUB separatelly in that time). 

So I went in my epic journey, installed Ubuntu 12.04 over the 11.04 and everything went fine. GRUB showed up Ubuntu and Windows 8 (on /dev/sda1), which I thought was very strange because my Windows 8 was on /dev/sda3 at that time. But everything worked well. When I chosed to boot up Windows 8, the Windows boot screen showed up, asking me to boot Windows 7 or 8. Perfect.

Then, I went into Ubuntu, installed GParted and deleted Windows 7 (/dev/sda1), moved Windows Stuff (/dev/sda2) to the left, increased it to have 960 GB, moved Windows 8 (/dev/sda3) to the left and increased it all the way to the right, totallizing 320GB on it. One problem ocurred: my PC rebooted for no apparent reason in the middle of the movement of "Windows Stuff". Nothing much, though, all I did to fix it was use "chkdsk /f" on Windows 7's Installation disc (I had no Windows 8 disc at the time, lol). Then I continued my move/resize operation and everything went fine.

Then, boom, when I selected "Windows 8 (on /dev/sda1)" on GRUB, it said that such partition didn't exist. Then I realised the shat I just did. /dev/sda1 was now Windows Stuff, not Windows 7 as it was =( As I had no knowledge that GRUB was a separated thing from Ubuntu at that time, I reinstalled Ubuntu completly. After that GRUB didn't even existed. My PC booted up directly to Ubuntu (which was quite freaking fast, by the way! Loved it, but I need my windows to play some games... =/ ). Then I searched the web and found [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Used its Recommended Repair. Now GRUB at least appeared, but no Windows 8 still.

I was really demotivated, but I found a good [thread]("http://chakra-linux.org/bbs/viewtopic.php?id=8501") on Chakra forum's. Tried almost everything on it, but some variables in the storyline there made it impossible for me to fix the problem like the user did there. I tried the first thing: "force" Windows 8 to boot up. Used this command lines (pressing "c" at GRUB):

```
insmod ntfs
set root='(hd0,msdos3)'
ntldr /bootmgr
boot
```

(For some reason, Windows 8 was /dev/sda3 at that time O.o)

That way Windows 8 booted up, but gave me a scary error:

[IMG]https://lh3.ggpht.com/-ik-lXpTSLdY/UJSkV6e3n3I/AAAAAAAAA1E/juP9DZdv8PI/s1600/Error+0xc000000f.jpg[/IMG]

Although I got this image from google images, it's the EXACT same error as mine. Of course I searched the internet's nooks and crannies and found some "solutions". I started by finally finding my Windows 8 Installation Disc, booted up from it and ran the "Repair Your Computer", or "Automatic Repair". Waited, waited... then it said that it couldn't solve my problem. Tried to boot up GRUB, run those commands again and the same error showed up. Then I went into the command prompt (on the W8's disc), and ran these commands:

```
diskpart
list disk
select disk 0
list partition
select partition 2
detail partition
active
```

Rebooted, no Windows 8 on GRUB. Forced boot, same error. Then, command prompt again:

```
bootrec /fixmbr
bootrec /fiboot
```

Rebooted. Same old, same old. Prompt, here we go again!

```
bootrec \scanos
bcdboot C:\Windows
```

Nothing again. Really sad. Searched the int3rwebz again, found some stuff and tried them. Cmd again, tried this there:

```
bootrec /fixmbr
boot /fixboot
bootrec /scanos
bootrec /rebuildbcd

```
Then the cmd gave me the error: "The requested system device cannot be found".

After that, I tried this:

```
bcdedit
bcdedit /set {default} device partition=c:
bcdedit /ser {default} osdevice partition=c:
bcdedit /set {bootmgr} device partition=c:
```

But I couldn't even proceed, because after I typed "bcdedit" then enter, cmd gave me this error: "The boot configuration data store could not be opened. The requested system device cannot be found".

My last option I could think of was to "refresh" windows from its installation disc. But when I chose that option, an error appears: "The device windows is installed is locked. Unlock it before refreshing", or somethin in those lines.

That's the end of the story. Everything I did to try to fix my problem is in this post. Nothing worked. Now my HDD setup is as showed in the first image. What should I do? I really tried hard but nothing seems to work. I want my windows back and my Ubuntu 12.04 working :'(

I'd be greatful for any form of help! Thanks!

---

