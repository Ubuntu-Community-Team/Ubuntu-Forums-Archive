---
title: "Installing NVidia on Feisty"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by Eniac on 2007-03-16
Ok, so ive read countless threads in the forums (ok not COUNTLESS but many) about installing nvidia cards on edgy/feisty.

but none of them solved my problem. the thread that came the closest i think is this one but no cigar
[http://www.ubuntuforums.org/showthread.php?t=384832&highlight=nvidia+kernel](http://www.ubuntuforums.org/showthread.php?t=384832&highlight=nvidia+kernel)

ive installed the xorg drivers, ive installed the new sources, its all there.

but when i run envy to install nvidia drivers it doesn't recognize my card, i know its an nvidia so i say "yes" to force it and then bam, black screen 'o nothin' happenin'

To tell the truth, i am unable myself to know for sure WHICH nvidia it is. This is the best spec i was able to get from the manufacturer 

NVIDIA GeForce6100-based. 2D/3D graphic engine

its an onboard card and its somehow associated to the MCP61 chipset from nvidia because when loading a gentoo liveCD it mention mcp61 in the name of the card.

So! i went to nvidia, tried to download the nForce MCP61 drivers for linux but im not sure what to do because ubuntu is not in the list of supported releases

[http://www.nvidia.com/object/linux_nforce_1.21.html](http://www.nvidia.com/object/linux_nforce_1.21.html)


I've also tried installing video drivers from nvidia but i can't! because it requires the header files and they're not out yet (.20 kernel - feisty)

... but i need feisty to have my network card work.


im going in circles here and im getting confused as to where to look.

Anyone can help ?

---

### Post by garybrlow on 2007-03-17
Nforce drivers are for built for specific NVIDIA video cards. Make sure first if your card is really an Nforce card or a GeForce one. You said its an NVIDIA GeForce 6100-based 2D/3D graphic engine according the manufacturer so with that you should use GeForce Drivers found here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html). Refer to howtos for other details. Compilation and use of  official NVIDIA work fine under feisty. The video section of the forums have a sticky for installing NVIDIA cards using official drivers.

Cheers!!!


GaryBrlow :biggrin:

---

### Post by bulldog on 2007-03-17
Just install the restricted modules for your kernel and the nvidia-glx driver.

Works for me with Beryl and emerald.

---

### Post by ecobird on 2007-03-17
work not on 64 bit

---

### Post by Eniac on 2007-03-19
Yeah, didn't manage to get it working yet.

I figure that i am either just too new to ubuntu/linux yet to make it work right or its really not supported by edgy/feisty yet (my hardware i mean) because gentoo sees it fine. but i dont want to switch to gentoo because its too much for what i understand of linux yet. all i wanted was a nice (free) web server and its gonna do that just fine.

Its probably just a matter of time so ill wait. its not like i really need the video interface anyway since this will be a web server. 

It was something that was bugging me and i would have rather have it solved but that doesn't matter, i know ill get more comfortable over time and things will be ok then.

---

