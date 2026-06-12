---
title: "Dual installation Windows 8 and Ubuntu 13.04"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by jagojago on 2013-05-02
Hi
I installed today Ubuntu 13.04 alongside a Windows 8 installation

Installed:
Windows 8 is installed on a Samsung NP700Z5A notebook UEFI and GTP partitioned.
The system has "TWO" disks, an SSD 256 Gb and an internal "memmory disk"  I used it for windows swap area totally

What I did:

I installed Ubuntu 13.04 from USB/EFi on a free partition manually assigning "/" (root) and a swap partition  (sda6 & sda7)


[http://elrebollar.org/images/ubuntu13/Boot-Info_2013-05-02__15h22.txt](http://elrebollar.org/images/ubuntu13/Boot-Info_2013-05-02__15h22.txt)
[http://elrebollar.org/images/ubuntu13/Screenshot-1.png](http://elrebollar.org/images/ubuntu13/Screenshot-1.png)
[http://elrebollar.org/images/ubuntu13/Screenshot-2.png](http://elrebollar.org/images/ubuntu13/Screenshot-2.png)

To my surprise after install the system booted to windows 8 (I wast waiting the ubuntu interface)
At the installation I select to install the grub at /dev/sda
I have no brub to select from at boot

Any good ideas?

TIA

Jago

---

### Post by oldfred on 2013-05-02
With a UEFI install, I do not think selecting sda makes any difference ( a good thing). The installer correctly installs grub into the efi partition. It looks like you have grub installed to efi partition but only the standard version not secure boot version.

If you go into UEFI (not Windows) and choose ubuntu from boot choices does it boot? It should have added ubuntu as a new boot option along with Windows and all the hardware choices.
Do you have secure boot on or off?
Some will not boot Windows with secure boot off. Even if they should. Some systems will.

---

### Post by jagojago on 2013-05-02
Hi, thanks for your response
I don't have any possibility to select any "software"/"OS" entry at bios level.  I can only select from disk /from DVD or from USB sticks.
And No t grub menu is present

Or I am missing something elementary?

TIA

Jago

---

### Post by oldfred on 2013-05-02
This user for some reason had two entries for Ubuntu.
You should see ubuntu in both UEFI and using one time boot key (f12 on my BIOS system).

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by jagojago on 2013-05-03
Hi oldFred, just again thanks for your reply

Mine don't have such a boot key option (to look for efi partitions).  Only devices are shown there but nothing to point to a "efi" file to boot from.
Before using EFI and GPT on this notebook, I had windows 7 and Ubuntu 12.04 running perfectly with a grub menu

Try to repair it using "boot-repair" botted from DVD?  Any other idea to repair it without using a "GUI" tool ?

Tia

Jago

---

### Post by oldfred on 2013-05-03
The BootInfo report uses this script and is the first part. BootInfo includes more efi info, but this may help.


 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in advanced  edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jagojago on 2013-05-03
OK, I will test it on the weekend and give my results
Thanks ;-)

---

### Post by jagojago on 2013-05-25
OK, I'm back again, just a little bit late :) Still having the same problem .........   ;-( I can now boot using rEFINd ([http://sourceforge.net/projects/refind/?source=directory](http://sourceforge.net/projects/refind/?source=directory)), really good tool, but I still looking for a workaround/touch to boot from a "grub-like" menu direct from my sda disk [http://paste.ubuntu.com/5697965/](http://paste.ubuntu.com/5697965/) any ideas? TIA Jago

---

