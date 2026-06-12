---
title: "Sorting out the hard drives on install"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by ubuntu1sttimer on 2007-11-02
Have an computer that has Dapper on it with a 15 gb drive and a 150 gb drive. The later is used with Samba as a file server for the local network. The 15 gb drive got full and it appears that Dapper may have continued to write to it and now it will not allow anyone to  log on. 

Have added a 300 gb drive that I want to use for the system and swap on 7.10. However I would like to try to recover some of the files that may be left on the 15 gb drive and keep the data on the 150 gb drive. 

If I install the 300 gb drive as the master drive, will the standard 7.10 install format and partition  it without making any changes to the other drives? Will the other drives and partitions be mounted or will I have to do that myself after the install?

Any info would be most helpful. 

Dave

---

### Post by dantrevino on 2007-11-03
I wanna say the installer will detect existing filesystems and not overwrite them, but I cant remember specifically testing this myself.  Maybe someone can chime in with a definitive answer....So...

Best thing to do, IMHO, is pop out the other two drives, install on your 300GB, then put the other two in and mount them manually.  Then you can copy your files around without worrying about the install process.

dan

---

### Post by ubuntu1sttimer on 2007-11-03
Thanks dantrevino,

Have not found much on what happens to drives during installation. As you suggested, I can add the drives later, but wanted to let the system do it so they would be mounted in the "standard" manor. However, do not want to risk loss of existing data. 

Have not been any other replies so it appears that this is an area with limited information available. Will do it as you mentioned and hope I get it close to the standard locations.
Dave

---

