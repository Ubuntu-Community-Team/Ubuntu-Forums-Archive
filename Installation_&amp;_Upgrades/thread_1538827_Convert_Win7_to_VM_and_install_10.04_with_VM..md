---
title: "Convert Win7 to VM and install 10.04 with VM."
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by cocamoxb on 2010-07-25
So I received my corporate laptop with Windows7 installed and all the nice bloatware that they love so much. I'd like to take a snap shot of the existing install. Then I'd like to wipe the drive and put a fresh Ubuntu 10.04 on it and install some fancy VM software. Then, I'd like to boot up that fancy new VM and restore the Windows7 snap shot to the VM.


Any ideas or proven process for this? Thanks in advance.

---

### Post by ServerStorm on 2010-07-26
Hi cocamoxb,

I would recommend using Acronis to create an image; easy to use and great with a wide berth of hardware. 

Using Acronis you will be asked what you want to image. Make sure you image the boot record and the O.S. drive. It will ask the size the image should be so make sure you leave enough for the O.S., 3rd Party Software and Data. You might want to format a separate partition as NTFS that is not part of the Acronis image that you then mount in Linux and add it as a drive on the virtual box - this is good for sharing music, videos etc between the two operating systems. I haven't checked in a while but Acronis used to offer a free trial. If this is still the case then you could use it to do this.

Once you have created the image, try restoring it too see if it works. Make sure that your corporate I.S. department could restore the original image if you run amuck.

If your image works well then use the Live Ubuntu CD and install Ubuntu. Tell it to use all of the drive and not install beside the Windows 7 that will be installed from the Acronis test. This will install ubuntu over your entire disk space.

I have run Windows 7 on Sun's (Oracles's) Virtual Box and it performs OK, enough so that I would recommend it. If you have enough RAM, make sure you allocate 1gig otherwise it will likely be sluggish. There are some fairly good tutorials on running Windows 7 in Virtualbox, just search for it.

You will create a new VM, give it RAM, configure HD space (should equal at least the size of your image), audio and peripherals. If you don't get it all right the first time don't worry you can change features of the VM at a later date if needed.

Hope this helps. 

Regards,
Steve

---

### Post by cocamoxb on 2010-07-26
Steve,

Acronis sounds like what I'm looking for. I literally only want the default install because I will need it for only two things, HR related websites, and one internal program that doesn't work well with Firefox. I will only boot up the VM when I have to access those two things. I've already got Ubuntu working with everything else corporate.

Thanks a ton and best regards.

cocamoxb

---

