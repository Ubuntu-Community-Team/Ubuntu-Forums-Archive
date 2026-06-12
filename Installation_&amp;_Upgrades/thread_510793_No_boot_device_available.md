---
title: "No boot device available"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by germanboy on 2007-07-27
I have successfully made my computer unaccessible.
	](*,)
My problems started when i tried to make ndiswraper work. Eventually me and my friend discovered that there was something wrong with libc6. Figuring it was a problem with the live cd we installed ubuntu with he told me to reinstall ubuntu. I don't really know what i am doing so when i went to reinstall ubuntu i decided to do it the same way that i installed it. I tried to delete the partition on which ubuntu was on. but when i went back it never registered a change. In an attampt to make it register a change I stupidly added the free space back to ntfs then i tried  take it back out....ever since ntfs won't let me repartition it.

I gave up and just tried to reboot... Grub error 17 popped up. My friend told me that when i deleted ubuntu i deleted grub...didn't think of that before hand. #-o Hoping that reinstalling linux would fix grub I tried repartitioning ntfs a couple more times.Basically it took two hours then the partitioner crashed. When i gave in that that wouldn't work I tried to install ubuntu on the 1.5 Gigabytes that had previously been the swap. I don't quite know if it worked or not all i know is that it became Grub error 15 instead.

Instead of trying to fix grub I decided to try and fix windows by using the recovery disk and typing in Fixmbr(I saw this advice given in a somewhat similiar case). When I typed it in it told me that i had an non-standard or invalid master boot record.  It also told me not to continue unless my computer wasn't working....it wasn't so i continued. It told me that it fixed my master boot record.

I rebooted and an error message popped up:

No boot device available -
  strike F1 to retry boot,F2 for setup utility

If you know how i can fix this please help me. Thanks

---

### Post by kyphi on 2007-07-28
> I have successfully made my computer unaccessible.

Yes, so you have.

You do not say if both operating systems were on the one drive or if you have two drives.  If you can install Ubuntu on its own drive there would be fewer problems in the future but make sure that both drives are the same, IDE or SATA connection.  

You will have to reinstall Windows as well as Ubuntu if you want both systems.  If you only want Ubuntu, just put the live Cd in your optical drive and Ubuntu will do the rest.

If you want both systems, you will have to install Windows first and Ubuntu second.  GRUB installs on both systems, that is Windows as well as Ubuntu.

Is that enough to get you started?

---

