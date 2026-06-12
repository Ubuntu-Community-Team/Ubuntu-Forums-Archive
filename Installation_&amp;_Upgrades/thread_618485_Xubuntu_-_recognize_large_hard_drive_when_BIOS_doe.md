---
title: "Xubuntu - recognize large hard drive when BIOS doesn't?"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by jrollf on 2007-11-20
I have an older Slot A Athlon 1Ghz running on a Gigabyte motherboard.  I want to add a 750GB to 1TB 2nd hard drive for data storage.  

I'm pretty sure that the bios on this old motherboard will not recognize this large of a hard drive.  However, I've read a few posts that have hinted that as long as Linux is booting ok on a smaller drive, then Linux doesn't care what the bios of the computer sees and will be able to use the large 2nd hard drive. I have Xubuntu on a 30GB primary hard drive and it will stay there, so booting won't be a problem.  

Is what I read correct?  Can I have a large 2nd hard drive that is used just for data storage that bios doesn't recognize?  Or do I need to go down the path of adding a pci host card for the large hard drive?

Thanks,

---

### Post by Craigus on 2007-11-20
It's hard to be sure, because some IDE controllers themselves cause limitations.

The usual advice (if booting from the large drive) is along the lines of:

> Arrange for /boot to be mounted on its own small 
> partition. Make sure the highest cylinder number of /boot is below the 
> BIOS limitation.

If the controller can handle the drive, then the linux kernel can.

Here's some general background information:

[http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm]("http://www.dewassoc.com/kbase/hard_drives/hard_drive_size_barriers.htm")

You could always try it and see. If it doesn't work, you could then get the controller card.

---

