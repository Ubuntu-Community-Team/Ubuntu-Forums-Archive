---
title: "Error while installing grub2 at HP 250 G6 laptop"
date: 2019-02-13
forum: Installation &amp; Upgrades
---

### Post by mikolajcieszczyk on 2019-02-13
I'm trying to install Ubuntu at HP laptop for long time. Users at  polish community was trying to help me but they didn't find a solve.


  I don't have nothing on the disk right now (it mean no Windows etc). I was trying to install Ubuntu 18.10 and newest version of Linux Mint.


  Case is simple: [B]during installation it is stopping in the  moment "Installation of grub2..." and don't go ahead. 

[/B]
I think and hear that this  is general problem with new HP laptops.

  **Things i did to solve this problem** (which of course didn't worked):
  
[LIST]
[*]re-burn LIVE USB (it works on my second laptop) 
[*]make every combination with on/off secure boot and legacy support 
[*]partitioning disk at every combination and let to do this ubuntu, making flags, mounting points etc etc 
[*]did format and reset disk 
[/LIST]

 **This is my boot-info:**

  [URL="http://paste.ubuntu.com/p/HvfvVzMkz6/"]http://paste.ubuntu.com/p/HvfvVzMkz6/
[/URL]

  Laptop HP 250 G6, Intel Celeron CPU N3550 @ 1.10GHz, 4GB RAM, BIOS InsydeH20

What to do mates?

---

### Post by yancek on 2019-02-13
Your boot repair output shows two installations (or partial installations) of Ubuntu 18.04 on sda2 and sda4.  Some necessary boot files (grub.cfg) are not showing which doesn't necessarily mean they are not there.  On a newer HP, hitting the Esc key on boot then the F9 key should give you boot options.  Do you see an option to boot from EFI file?  If so, you should select the one which says ubuntu or has the number  Boot0000.  Do you see any options there, if so what are they?  Also in the BIOS, try the suggestion by boot repair:

> Please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file!
The file above is:  /EFI/ubuntu/grubx64.efi

I would try disabling Legacy/CSM and Secure Boot in BIOS.

---

### Post by oldfred on 2019-02-13
HP often only wanted to boot "Windows Boot Manager" by description.
One work around was to use the hard drive or fallback boot entry which uses /EFI/Boot/bootx64.efi.
And if only Ubuntu you can create a UEFI boot entry with efibootmgr that says "Windows Boot Manager" but actually boots Ubuntu using /EFI/ubuntu/shimx64.efi.

Have you updated UEFI. Some have said that newer UEFI works better and is not as restrictive on descriptions.
Work arounds shown in link in my signature.

---

### Post by mikolajcieszczyk on 2019-02-13
After pushing Esc it went me to this menu:

[http://www.dropbox.com/s/dzn60401hkhx1ur/Ubuntu-install-2.jpg?dl=0](http://www.dropbox.com/s/dzn60401hkhx1ur/Ubuntu-install-2.jpg?dl=0)

Of course i chose Boot from EFI file and it give me this:

[http://www.dropbox.com/s/8vfwljto9hoaoij/Ubuntu-install-1.jpg?dl=0](http://www.dropbox.com/s/8vfwljto9hoaoij/Ubuntu-install-1.jpg?dl=0)

From your instructions I deduce that you mean about that first option so i chose it and get this:

[http://www.dropbox.com/s/x3ct5qy6olwafc4/Ubuntu-install-3.jpg?dl=0](http://www.dropbox.com/s/x3ct5qy6olwafc4/Ubuntu-install-3.jpg?dl=0)

[http://www.dropbox.com/s/klp2g6w47lz49lw/Ubuntu-install-4.jpg?dl=0](http://www.dropbox.com/s/klp2g6w47lz49lw/Ubuntu-install-4.jpg?dl=0)

If i click <BOOT> i get this:

[http://www.dropbox.com/s/ks4gns01cjwrtp9/Ubuntu-install-6.jpg?dl=0](http://www.dropbox.com/s/ks4gns01cjwrtp9/Ubuntu-install-6.jpg?dl=0)

But if I click <ubuntu> i get this:

[http://www.dropbox.com/s/10f99dem4ma3ef2/Ubuntu-install-5.jpg?dl=0](http://www.dropbox.com/s/10f99dem4ma3ef2/Ubuntu-install-5.jpg?dl=0)

So i'm pushing grubx64.efi and go to that screen which I saw during my struggling with that problem but completely don't know what to do with this:

[http://www.dropbox.com/s/5qw2q0c4bt9xfmq/Ubuntu-install-7.jpg?dl=0](http://www.dropbox.com/s/5qw2q0c4bt9xfmq/Ubuntu-install-7.jpg?dl=0)

---

### Post by yancek on 2019-02-13
Did you have the same result when you selected the 2nd entry on the page showing No Volume Label?  If so, do you get the same options and the same results.  If boot repair output is accurate, I would not expect to be able to boot as there is no grub.cfg file.  You do have the grub.cfg file in the EFI partition pointing to sda2 with the correct UUID so I'm really not sure why there is no grub.cfg file on sda2.  I have no other ideas so unless oldfred or someone else has a suggestion, you might try re-installing and taking careful notes of each step, particularly any warning/error messages you receive.

---

### Post by mikolajcieszczyk on 2019-02-13
> **yancek said:**
> Did you have the same result when you selected the 2nd entry on the page showing No Volume Label?  If so, do you get the same options and the same results.  If boot repair output is accurate, I would not expect to be able to boot as there is no grub.cfg file.  You do have the grub.cfg file in the EFI partition pointing to sda2 with the correct UUID so I'm really not sure why there is no grub.cfg file on sda2.  I have no other ideas so unless oldfred or someone else has a suggestion, you might try re-installing and taking careful notes of each step, particularly any warning/error messages you receive.

When i select second option i get only <boot> options and behind it are bootx64.efi or grubx64.efi to choose.

I was installing carefully for I think fifteen combinations and there was no effect...

---

### Post by oldfred on 2019-02-13
While grubx64.efi should work, I normally use shimx64.efi which is for Secure Boot, even though I do not have UEFI Secure Boot on.

Your Lilo install for MBR boot may be confusing things. But not easy or save to remove it.
You would have to use dd and write 0 to MBR, but not protective partition table in MBR. DD's nickname is data destroyer.

Did you update UEFI?

Lets add this entry to UEFI.
 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

