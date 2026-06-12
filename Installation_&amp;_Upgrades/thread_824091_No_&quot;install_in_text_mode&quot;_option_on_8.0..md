---
title: "No &quot;install in text mode&quot; option on 8.0.4 Alternate cd?"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by bigteks on 2008-06-09
The docs say the alternate CD should have a menu selection of "install in text mode". I'm not seeing this. Has this changed in 8.x? Or am I looking in the wrong place? Or is something wrong with this CD?

I'm having trouble installing a minimal ubuntu 8.0.4 on my laptop, in other words some other way besides the live cd. Live CD works fine. But when I tried the server or fluxubuntu cds then whatever happens after the linux kernel loads, the screen goes blank and never comes back.

So I'm trying the alternate cd, text mode to see if it does anything different. But it's not giving me the install menu that the docs say the alternate cd should have.

Any insight is appreciated.

---

### Post by herteljt on 2008-06-09
Check to see if you downloaded the correct iso image from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ?  

You need to tick the little box that says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."  

If you select your download location and then click start **without** checking the box you'll be downloading the live cd.  The alternate cd iso should have a file name of ubuntu-8.04-alternate-i386.iso

As long as you are doing a fresh install, I might also recommend creating a separate /home partition.  It makes for easy reinstall/upgrades.

Here is a link with some info:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Hope this helps!

---

### Post by bigteks on 2008-06-10
Thanks - yeah, it was definitely the alternate iso, at least that's the filename it came down with. I used the amd64 version but it should work the same right? If anyone has an answer on this issue I'll retry that approach but right now I'm plowing ahead with the live CD because at least I can get it installed.

What about removing unnecessary stuff? I'm running vmware server, bluetooth (mouse), wireless networking and Sprint broadband wireless (pppd, usb). So I need to keep the services for that stuff.

But right now it's using over 600MB of memory and I'd like to get that way down so most of the memory is available for the VMs. Any pointers on how I can go about figuring out what to drop?

---

### Post by herteljt on 2008-06-10
One more question, did you verify the iso using md5sum?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)


As far as removing things, there are quite a few programs you can remove ( openoffice, gimp, for example)

Go into System > Administration > Synaptic Package Manager 

In the left window change from All to Installed and you will see the right window populated with installed software.  Be careful :)

---

