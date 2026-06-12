---
title: "Twat here!"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by happyhacker on 2007-01-01
Ok,  want a linux server. I have a dell optiplex 110 800Mhz 80Gb 500Mb ram. It has an imported drive with windows (to be deleted). It has a cd/dvd drive I have set to boot first from. I have browsed this site but being bit green have not seen what I need to download to chuck a cd/dvd in to get it started. I have no floppy so no chance to do anything with the machine as it stands.

So what do I download to just copy to cd/dvd and away I go!?

Thanks

---

### Post by riven0 on 2007-01-01
If I'm reading this correct, you want to download the server edition? Just [go here]("http://releases.ubuntu.com/edgy/") and choose Server Install. Make sure you burn the .iso at a low speed to prevent errors, (4 - 6kbs, for example). And it has to be burnt as an iso image.

---

### Post by Tomosaur on 2007-01-01
If you have no experience with Linux, do not download the server CD, as you'll be in a command line and won't know what to do. Download the ordinary Ubuntu desktop edition and familiarise yourself with Linux before having a go at a server.

If you know Linux, knock yourself out :)

---

### Post by happyhacker on 2007-01-03
Thanks I will not want to use the cmd to start with. How easy is it to add the server features LAMP later so I can have a desktop WITH server additions?

---

### Post by aberry5555 on 2007-01-03
I use Ubuntu Desktop on two DNS servers and I also use another gui based linux for apache and php. Ubuntu is astonishingly easy to set up with extra packages, if you look through the menus you can find the software install or upgrade button which downloads what you want from the repositories. If you can't find the right programs then open a terminal and type "sudo synaptic" this will open synaptic, the main package installer for many x systems, which has a list of about 5-10k pieces of software. make sure you type "sudo" before synaptic, though, or else itll just tell you to sod off :p Also, if you decide to learn how to do it without a gui (for security reasons; guis are inherently much easier to hack) then look in to a bit of software called "webmin" which lets you log in to your server(s) from any computer via self-serving webpage and which lets you control nearly every aspect of the server, including most LAMP settings.

---

### Post by happyhacker on 2007-01-03
So I assume that you have a GUI version of UBUNTU with the LAMP packages, OK a bit daunting. Thing is at the moment I have SUSE9.1 (hope I can swear on this forum) running SAMBA. Is this available with UBUTU?

I actually have 2 old PCs so will run UBUNTU on one I am preparing. It has an 80Gb hdd and ethernet so should go OK. I assume copying downloaded ISO to CD and then just configure BIOS to boot from CDROM will work?

Will the SUSE and UBUNTU work together on a network?

Which would be the best one to configure for Broadband?

Will Linux work with a BT Broadband HUB?

Thanks

---

### Post by aberry5555 on 2007-01-03
Since a router is just a very basic switch with a WAN modem attached it will work fine. A BT broadband router serves up internet to Xboxs so Linux won't have problems :p. If your bt router has DHCP, which I'm sure it will do, it should just be a matter of plug and play, like windows. I have never tried SAMBA on ubuntu but there should be no reason at all that it wouldn't work OK. Again, try using the Webmin Program as it will give you a graphical interface for things like SAMBA and the LAMP setup you want. Ubuntu and Suse should work fine on the same network, depending on whether you want them to show up on your windows network (using samba) or on a linux network. I've never personally done any proper Linux intranet network, only fiddled with samba so you'd have to ask someone else on that one, though I presume Linux protocols are the same throughout alot of distros so it shouldn't be a problem either.

---

