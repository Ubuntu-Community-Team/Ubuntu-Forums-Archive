---
title: "upgrade 16. something to 18.04 boot problems"
date: 2018-11-11
forum: Installation &amp; Upgrades
---

### Post by benlyboy on 2018-11-11
Hi I just up graded my desktop from 16 to 18.04 using the upgrade option on the updates app. my system now freezes when it gets to the purple screen that has ubuntu on it, it does it right at the point when the causer appears  on the screen.

How ever if I go in through recovery mode then go on to select boot normally it boots up quiet happily. s

would I be right in thinking I am dealing with some kind of video driver problem?

If so how do i go about fixing it?

thanks  :-)

---

### Post by QIII on 2018-11-11
Hello!

It would be helpful if you would post your hardware specs and let us know if you had a propriety driver of any sort installed before you upgraded.

---

### Post by benlyboy on 2018-11-11
Yes sorry should have given some system information.
The computer is an old Dell that we have had for quite some time I actually know very little about its specs, so I ran lshw. This is some of the resulting information. 
I did notice two things my self from this info, first you can't see on here but the listings for the video were the only ones in red. 
The second is as you can see there are two of them.

i should probably add there is no additional video card installed, only the motherboards  on board video. 

id:	 there
graham-optiplex-755
description: 	Desktop Computerinstalled
product: 	OptiPlex 755
vendor: 	Dell Inc.
serial: 	JYRN1J1i
width: 	64 bitsyes 

id:	
display:0
description: 	VGA compatible controller
product: 	82Q35 Express Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2
bus info: 	
pci@0000:00:02.0
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	msi pm vga_controller cap_list
configuration:	
latency	=	0
resources:	
memory	:	fea00000-fea7ffff
ioport	:	ec90(size=8)
memory	:	d0000000-dfffffff
memory	:	feb00000-febfffff
memory	:	c0000-dffff

id:	
display:1
description: 	Display controller
product: 	82Q35 Express Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	
2.1
bus info: 	
pci@0000:00:02.1
version: 	02
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	0
resources:	
memory	:	fea80000-feafffff

Thanks again

---

### Post by benlyboy on 2018-11-11
Ok did some research on line and it seems that 18.04 has an issue with older intel video chips. 

The funny thing is that if I boot into recovery mode then from there go ahead and select boot normally I get a warning that says something like "some video drivers require full boot if the system fails to boot go ahead and restart your computer" something along those lines.

The fact that its working great when I boot this way make me wonder if a selected driver isn't loading when I boot this way, and the system is then falling back on a backup driver. 
The graphics are perfectly fine in this mode. so I'm wondering if maybe the answer is to deselect that main driver and let the backup take over?

is this a possibility?

---

### Post by benlyboy on 2018-11-12
Moved this question over to the general page as i no longer think its a upgrade issue.

---

