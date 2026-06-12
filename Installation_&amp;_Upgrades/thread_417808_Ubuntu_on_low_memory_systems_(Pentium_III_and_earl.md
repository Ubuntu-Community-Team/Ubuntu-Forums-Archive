---
title: "Ubuntu on low memory systems (Pentium III and earlier machines, with 32-192 MB RAM)."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by kagashe on 2007-04-21
Hi,

I have read the instructions on this [page]("https://help.ubuntu.com/community/Installation/LowMemorySystems") regarding installation on low memory systems.

This page is recommending to use the alternate (install) CD and chose  "Install a server" on Ubuntu 6.06 and  "Install a command-line system" on Ubuntu 6.10.

I assume that the option "Install a command-line system" would be availabe in Ubuntu 7.04 alternate (install) CD as well.

This page also talks of UbuntuLite. There is another page regarding installation of UbuntuLite [here]("https://help.ubuntu.com/community/InstallingUbuntuLite").

This page recommends server CD for all versions dapper and after.

The difference may be there because the pages are maitained by different people but what is the real difference?

I don't have any use for Ubuntu "server" CD but "alternate" CD is very useful because it can install the complete desktop on the machines which have adequate RAM.

I already have alternate CD of Feisty.

What are the pros and cons of using "alternate" or "server" CD for such installations which will use IceWM, Fluxbox or Openbox?

kagashe

---

### Post by K.Mandla on 2007-04-21
Yup, Feisty has a "command line system" install option, but again, that only appears on the alternate CD. I don't believe it's possible to install a command line system from the desktop CD (unless someone can correct me on that).

The difference between the server CD and installing a "server" (a "command line system") is minimal; if I remember right, you might get an option to install a LAMP server with the server CD, whereas the alternate CD is strictly a base-level Ubuntu installation. (Of course, that too might have changed with Feisty; I haven't downloaded all the variants and installed from them yet. ;) )

I think you'll get basically the same results from an alternate "server" and a server CD installation. 

Did I answer your question? :D

---

### Post by kagashe on 2007-04-22
> **K.Mandla said:**
> Yup, Feisty has a "command line system" install option, but again, that only appears on the alternate CD. I don't believe it's possible to install a command line system from the desktop CD (unless someone can correct me on that).

The difference between the server CD and installing a "server" (a "command line system") is minimal; if I remember right, you might get an option to install a LAMP server with the server CD, whereas the alternate CD is strictly a base-level Ubuntu installation. (Of course, that too might have changed with Feisty; I haven't downloaded all the variants and installed from them yet. ;) )

I think you'll get basically the same results from an alternate "server" and a server CD installation. 

Did I answer your question? :DI am not talking about desktop CD. Yes, you answered the question.

I am trying to promote Ubuntu in India on home desktops and there are too many machines with 128MB RAM and below. 256MB RAM has become default for low cost PCs only recently. Adding RAM is also cheap now but there is always an arguement that Windows is working well with 128MB RAM then why not Linux?

I know about Damn Small Linux, Puppy and others but they are basically Live CD distributions and my idea is to promote Ubuntu which has so much support on this forum and on community documentation.

kagashe

---

### Post by K.Mandla on 2007-04-22
Have you looked at [Fluxbuntu]("http://www.fluxbuntu.org") by chance? It uses Ubuntu and adds the Fluxbox window manager, which makes it usable on machines that are far below the specs you listed. There are some other Ubuntu variants that might also work for you. (I see you already asked a question or two on the Ubuntu Lite Google Groups page. ;) )

---

### Post by kagashe on 2007-04-22
> **K.Mandla said:**
> Have you looked at [Fluxbuntu]("http://www.fluxbuntu.org") by chance? It uses Ubuntu and adds the Fluxbox window manager, which makes it usable on machines that are far below the specs you listed. There are some other Ubuntu variants that might also work for you. (I see you already asked a question or two on the Ubuntu Lite Google Groups page. ;) )
I have installed Fluxbuntu this morning (also have UbuntuLite on the other partition) and cheking it now. Yes, I asked the same question on UbuntuLite Google group and was informed to use the "alternate" Dapper CD (not to use Feisty).

It seems we have to wait for Feisty editions of Fluxbuntu and UbuntuLite.

I am impressed with Fluxbuntu Live CD since it is possible to install from it on 128MB RAM.

kagashe

---

### Post by DJiNN on 2007-04-25
> **kagashe said:**
> 
I am trying to promote Ubuntu in India on home desktops and there are too many machines with 128MB RAM and below. 256MB RAM has become default for low cost PCs only recently. Adding RAM is also cheap now but there is always an arguement that Windows is working well with 128MB RAM then why not Linux?

Well done for the promotion of Ubuntu in India, i trust it's going well?

As for Windows working well on 128mb of RAM, which version of Windows is that? I doubt very much if either Win2k or XP will work at all well on only 128mb, so you must be talking about something like Win98 perhaps?  Win98SE was (IMHO) one of the best OS's to come out of MS, but compared to a modern OS like Ubuntu or any of the other Linux distros, it's positively ancient! :)  

Even on a "Lite" system running IceWM, Fluxbox or OpenBox, you still have so much more than you ever had with Win98.

> I know about Damn Small Linux, Puppy and others but they are basically Live CD distributions and my idea is to promote Ubuntu which has so much support on this forum and on community documentation.

Both DSL & Puppy can be installed if need be, although they are nowhere near as easy to keep updated & running smoothly (at least not without some Linux knowledge & understanding etc) as Ubuntu.

Have you perhaps looked at Zenwalk as an alternative? Very light, very fast even in it's native install with XFCE and the quality of support & feedback from the forums is excellent.

Fluxbuntu is also a really great lightweight (But powerful) distro, but you can effectively achieve the same with Feisty by doing a Server (Alternate) install and then just adding stuff like OpenBox or Fluxbox & whatever other apps you require.

DJiNN



kagashe[/quote]

---

### Post by kagashe on 2007-04-25
> As for Windows working well on 128mb of RAM, which version of Windows is that? I doubt very much if either Win2k or XP will work at all well on only 128mb, so you must be talking about something like Win98 perhaps? Win98SE was (IMHO) one of the best OS's to come out of MS, but compared to a modern OS like Ubuntu or any of the other Linux distros, it's positively ancient! 

Windows XP works well with 128MB RAM. You have to go for "Selective Startup" in System Configuration. In fact that is the main reason why people are not willing to switch to Linux.

 kagashe

---

### Post by yoasif on 2007-04-25
> **kagashe said:**
> Windows XP works well with 128MB RAM. You have to go for "Selective Startup" in System Configuration. In fact that is the main reason why people are not willing to switch to Linux.I'm not sure that saying that cutting down the OS makes it "work well"... they would be much better off using even Windows 2000.

As far as your problem, I would install Xubuntu... it's very light, and with a fast processor (and limited) ram, can work very well. Using bum (boot up manager) to prevent some startup items from running may also be useful.

---

### Post by kagashe on 2007-04-25
> As far as your problem, I would install Xubuntu... it's very light, and with a fast processor (and limited) ram, can work very well. Using bum (boot up manager) to prevent some startup items from running may also be useful.

I have used Xubuntu 6.06 on 128 MB RAM machine. It is very slow on Intel Celeron 2.4 GHZ and 128 MB RAM if you compare with what Windows XP can do.

kagashe

---

### Post by yoasif on 2007-04-25
Honestly, if these are 2.4 Ghz machines, these machines would do extremely well with even Ubuntu with a small RAM upgrade. My brother used Xubuntu on an 866 P3 and 512 mb ram, and that was somewhat slow (with Flash) -- but your specs (aside from the RAM) completely outclasses an 866.

Is there no source for cheap/used RAM? Have you tried buying some secondhand, even? as far as Windows "running well" on such a low amount of ram... i'm guessing that these people are just running IE... IE is "built into" windows, whereas no web browser is built into the OS like IE is in windows -- it's a design thing that prevents the horrible malware problems that IE6/XP users often suffer from. 

If upgrading the hardware isn't an option (it would help a LOT), I would recommend trying to lighten the load even further by using apps that are friendlier with RAM usage -- this is hard to do on Feisty, for such a RAM starved machine, I would go with the dapper -- it'll be supported for a long time, and the packages are likely to be a bit older. Plus, there is quite a bit of documentation available for it. 

some ideas for lightening the ram load -- icewm as the DE, epiphany/opera as the web browser, the "gnome office" as the productivity apps, and again, bum to lighten the startup/services load.

---

### Post by DJiNN on 2007-04-25
> **kagashe said:**
> I have used Xubuntu 6.06 on 128 MB RAM machine. It is very slow on Intel Celeron 2.4 GHZ and 128 MB RAM if you compare with what Windows XP can do.

kagashe

That's strange. I have used Xubuntu on a PIII 1 Ghz with 128 meg, and it far surpasses anything that windows can offer. (XP that is) 

Windows is very snappy & fast when  you first start it up, but as soon as you start to weigh it down with apps &/or leave it on for any length of time, it starts to slow down & often fall over. :)

I'd still say that Zenwalk would be a good choice.

---

### Post by kagashe on 2007-04-26
> Have you perhaps looked at Zenwalk as an alternative? Very light, very fast even in it's native install with XFCE and the quality of support & feedback from the forums is excellent.
Installed Zenwalk this morning replacing UbuntuLite. I am impressed. I wonder whether I could "tweak" Xubuntu to get the same speed.

kagashe

---

