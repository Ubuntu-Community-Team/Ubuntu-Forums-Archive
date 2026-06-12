---
title: "Installing Ubuntu 11.04 on External HD with Intel BIOS"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by MattyOnIce on 2012-02-08
I am currently trying to broaden my horizons and learn Linux using a chasis, power supply, CPU, and motherboard from a friend of mine. I have a WD MyBook 500GB external hard drive that I originally thought I would be able to install Ubuntu version 11.04 on and get running but I am runnign into some major issues. 
 
I used this message board as a reference and I found only this link that matched the same issues I have: 
 
[http://ubuntuforums.org/showthread.php?t=1563699&highlight=puter+boot+lucid](http://ubuntuforums.org/showthread.php?t=1563699&highlight=puter+boot+lucid)
 
The error is in question is almost the same, with the only difference being that:
 
1. The computer does not give me a option to boot from CD after failure of bootup
 
2. The computer displays a "DHCP.... /" and rotates a slash at me before telling me that "Intel Boot Agent failed to find a bootable disk"
 
I followed the 13-step process to the letter with someone peer checking me the entire time, just as srs5694 offered in the referenced post. I followed it up by running the fdisk procedure to ensure that the bootflag is set. I compared my screen results to what tarahmarie said in her posts, and it was identical to what srs5694 said. The computer still returned the same error on boot. 
 
I also tried what srs said at the end of the post and zapped the GPT partition using expert mode on gdisk, then installing again and using UEFI by enabling it on my Intel motheboard. No avail.
 
I am hoping that someone can help me with this, and I would appreciate it. I know almost nothing about Linux, but unfortunately feel like a master about that referenced post, and have been working in the Windows enviroment for a long time. 
 
My greatest fear is the internal hard drive that is being shipped to me currently is also not going to be able to work. Any information needed I will provide.
 
Thank you in advance.
 
(In case it helps: Intel firmware version: 
[SIZE=2]dpp3510j.15a.0261.2007.0723.2348) [/SIZE]

---

### Post by oldfred on 2012-02-08
Intel motherboards often has BIOS that assumes Windows. Grub does not use a boot flag at all, Windows has to have a boot flag on a primary partition. 

I think I was in a thread with srs5694 where we had to add a boot flag to a gpt partition even though that is not per the gpt rules.

I use BIOS to boot and have several drives partitioned to gpt. I now create an efi partition as I may get a new computer in the near future that uses UEFI and also have a bios_grub partition for grub with BIOS in gpt drives.

Post boot info script. The test version has some fixes:

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Current version has some instructions if you need them:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Some simple things can be auto fixed with this and it runs the git/test version of boot script:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by MattyOnIce on 2012-02-09
Thank you very much for your prompt response.  I will be trying this after work and I will respond.

---

