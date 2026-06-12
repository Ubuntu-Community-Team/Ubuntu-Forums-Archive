---
title: "Change motherboard"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by captgadget on 2009-11-28
OK, I been given a Dell Optiplex GX280. I want to take the hard drives out of the GX270 and put them in the 280. If I use Synaptic> Generate Package Download Script and have to do a clean install will the script I saved reinstall the downloads I already have?

---

### Post by hirnwurscht on 2009-11-28
Hi captgadget,

i think your ubuntu will run even if you just swap the hdd over.
No need to reinstall.

Or do you want to add the GX270 hdd to the GX280 instead of replacing it?


Your way should work, too.

---

### Post by captgadget on 2009-11-28
I would like to take the exisiting hd from the 280 and replace with the hd from the 270 with Karmic already installed.

---

### Post by hirnwurscht on 2009-11-28
My suggested way without reinstalling:

1) Do a backup (either way!)

2) Swap harddrives

3) Boot

4) If there are no big hardware changes (like ati to nvidia graphic card) there should be zero problems and you are finished...

5) If something doesn't work you can still plug the hdd back in the G270 and have your old system starting normaly

---

### Post by cascade9 on 2009-11-28
That should work, but from a quick look on the Dell site it seems that the GX280 has SATA drives, the GX270 has IDE (40GB 5400RPM, 40-80GB 7200RPM) or SATA (120GB 7200RPM). If you put a 40GB 5400 into the GX280, you will probably notice the lower speeds on some tasks. Even a 40-80GB 7200 is slower than a SATA drive...as to if you would notice that, it depends.

[http://www.dell.com/downloads/us/products/optix/gx270_spec.pdf](http://www.dell.com/downloads/us/products/optix/gx270_spec.pdf)
[http://www.dell.com/downloads/global/products/optix/en/spec_optix_gx280_en.pdf](http://www.dell.com/downloads/global/products/optix/en/spec_optix_gx280_en.pdf)

---

### Post by captgadget on 2009-11-28
Good point - Thanks for pointing that out!!!

---

### Post by captgadget on 2009-11-28
If I install a new say 320GB SATA HD in the GX280 is there a way to clone my existing HD and copy over to the new SATA HD?

---

### Post by hirnwurscht on 2009-11-28
Yes, cloning is possible.

[http://clonezilla.org/]("http://clonezilla.org/")


It's like that:

Attach both drives to one computer.

Burn/Boot the Clonezilla LiveCD and clone the partitions.

Take care, don't mix up the drives ;)

This takes some time, 300GB can take 5hrs..

---

### Post by captgadget on 2009-11-28
Think I'll just leave things the way they are. I'd be going from 2.4Ghz to 2.8. Big deal!!!!

Thanks for everyone's input.

---

### Post by cascade9 on 2009-11-29
It kind of hard to tell exactly what CPUs are in either system (without part numbers anyway). If your going from, say 2.4 @ 533 FSB 512K cache to 2.8 @ 800 FSB 1MB cache, there is quite a difference. 

Doubling the cache and upping the FSB makes quite a difference. For myself, I went from a Athlon +2200- 1.8Ghz, 266 FSB 256K to a +2500- 1.8Ghz 333 FSB 512K and the difference was quite noticable. 

Mhz isnt everything. ;)

---

### Post by captgadget on 2009-11-29
Now you've got me thinking. FSB goes from 533 to 800 & cache goes from 512 to 1MB.

Just wish now there was an easy way to change the hds.

Thanks for making me think.

---

