---
title: "Installing multiple distributions on GPT disk &amp; LVM"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by kcy29581 on 2012-08-24
Hi all,

I am having some difficulty understanding how grub would work in my scenario with a GPT disk & LVM.

Scenario:
Step  1) I have a BIOS system, and my HDD is formatted with GPT; gdisk  reports it has a protective MBR. I created the following partitions:
    - 1 BIOS bios partition with equivalent type (ef02) & flag (bios_grub): /dev/sda1
     - 4 partitions for /boot, for Linux distributions that require them  (such as Fedora/CentOS/etc.), type 8300. I made these since I'm testing  various server distibutions: /dev/sda2-5
    - 1 LVM partition, type 8e00: /dev/sda6

Step  2) I installed Arch first with the / partition in a logical volume  within the LVM partition. I did not use a separate /boot partition, and  installed grub to /dev/sda with the following options (does grub  automatically use the BIOS boot partition, or did I have to point it  there?):
   # modprobe dm-mod
   # grub-install --target=i386-pc --recheck --debug /dev/sda
   # mkdir -p /boot/grub/locale
   # cp /usr/share/locale/en\@quot/LC_MESSAGES/grub.mo /boot/grub/locale/en.mo
Arch boots up fine and works.

Step  3) I now tried installing Ubuntu server, and used a logical volume for  /, and did not use a /boot partition. When it asked me where to install  grub, I was totally stumped; is it even possible to install grub to a  logical volume?

Questions:
 a) I want to use Arch's grub to  load all the other distributions, so where do I install their grubs? Am I  forced to use a separate /boot partition in my case?
 b) In [Step 2] above, should my second command point to my BIOS boot partition, instead of the GPT disk? It would become:
    # grub-install --target=i386-pc --recheck --debug /dev/sda1
 c) Is it possible to install grub to a logical volume within an LVM partition?

Many thanks for any help/info you can provide.

---

### Post by oldfred on 2012-08-26
I do not know LVM. 

But logically, you cannot install more than one grub to the MBR and the BIOS_grub partition is for core.img which is the extra space grub2 needs from the MBR to continue to boot. So any second installs may write into the bios_grub and cause issues.  With Ubuntu you cannot choose to not install, not sure about your other distributions. 

I also am real curious if grub2 is installed to a partition (Do not know if that works with LVM or not) whether it then also writes core.img into bios_grub which would in effect corrupt the grub in the MBR.

I would run lots of bootinfoscripts before and after every install and just be prepared to reinstall grub2 for the Arch install or which ever one you want in MBR.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Is able to search LVM partitions if the LVM2 package is install, Fedora needs to be mounted to see it with os-prober
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils
# unlzma is equivalent to xz --format=lzma --decompress.

The git/testing version has some fixes:
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

---

