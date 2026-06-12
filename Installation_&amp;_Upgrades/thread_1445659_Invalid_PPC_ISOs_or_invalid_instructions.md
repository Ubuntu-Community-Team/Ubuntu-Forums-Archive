---
title: "Invalid PPC ISOs or invalid instructions?"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by svu on 2010-04-02
I am trying to recover my Ubuntu (from broken 10.04 installation) on Power G4. The Superdrive is not functioning - so I am trying to give USB boot a try. The are instructions here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I am following them... Up to the point where hdiutil has to convert .iso to .dmg:

*Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/kubuntu.iso) Note: OS X tends to put the .dmg ending on the output file automatically.*

No luck. I am getting the error. Same thing actually happens with the release ISO 9.10. Tried on 2 Macs:

[FONT="Lucida Console"]$ hdiutil convert -format UDRW -o out.img lucid-alternate-powerpc.iso 
Reading Driver Descriptor Map (DDM : 0)…
Reading Apple (Apple_partition_map : 1)…
Reading Ubuntu 10.04 ppc                 (Apple_ISO : 2)…
Reading Ubuntu 10.04 ppc (Apple_HFS : 3)…
..............................................................................
Usage:	hdiutil convert -format <format> -o <outfile> [options] <image>
	hdiutil convert -help[/FONT]

With -versbose, I getting the error code 22

[FONT="Lucida Console"]DIDiskImageConvertWithDiskImage: converter returned 22

hdiutil: convert: result: 22[/FONT]

Any ideas? How could I make bootable flash?

---

### Post by lookup on 2011-03-12
> **svu said:**
> I am trying to recover my Ubuntu (from broken 10.04 installation) on Power G4. The Superdrive is not functioning - so I am trying to give USB boot a try. The are instructions here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I am following them... Up to the point where hdiutil has to convert .iso to .dmg:

*Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/kubuntu.iso) Note: OS X tends to put the .dmg ending on the output file automatically.*

No luck. I am getting the error. Same thing actually happens with the release ISO 9.10. Tried on 2 Macs:

[FONT="Lucida Console"]$ hdiutil convert -format UDRW -o out.img lucid-alternate-powerpc.iso 
Reading Driver Descriptor Map (DDM : 0)…
Reading Apple (Apple_partition_map : 1)…
Reading Ubuntu 10.04 ppc                 (Apple_ISO : 2)…
Reading Ubuntu 10.04 ppc (Apple_HFS : 3)…
..............................................................................
Usage:	hdiutil convert -format <format> -o <outfile> [options] <image>
	hdiutil convert -help[/FONT]

With -versbose, I getting the error code 22

[FONT="Lucida Console"]DIDiskImageConvertWithDiskImage: converter returned 22

hdiutil: convert: result: 22[/FONT]

Any ideas? How could I make bootable flash?

resurrection!

I'm encountering the same issue.  trying to make a bootable USB key and getting the same usage error as above.  oddly enough, I successfully converted two 10.10 .iso's to .img's, but two separate 10.04 .iso's have stopped me here.

did you manage to figure it out?  thanks for any info.

---

### Post by lookup on 2011-03-12
I guess my inclination now is that it's a sign of a faulty .iso.  I just downloaded a new one and the conversion worked fine.  it's strange though because the .iso that gave me the usage error burned to a CD and booted just fine.

---

### Post by kagerato on 2011-03-12
> **lookup said:**
> I guess my inclination now is that it's a sign of a faulty .iso.  I just downloaded a new one and the conversion worked fine.  it's strange though because the .iso that gave me the usage error burned to a CD and booted just fine.

You can check the ISO file against the MD5 or SHA-1 hash provided by the same server that you got it from.  When they match, there's an extremely high probability than the file is correct.

Here's one example mirror site:

[http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/10.10/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/10.10/release/)

Those are the wrong architecture and the DVD ISOs, but it's just an example.  See the MD5SUMS , SHA1SUMS, and so forth?  Those textfiles have the hashes in them.

The typical console programs used to calculate these hashes are called 'md5sum' and 'sha1sum', respectively.  (There are many programs which can do the job, however.  You needn't limit yourself to these.)

---

