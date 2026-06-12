---
title: "Dual boot 17.04 fresh install, stuck on grub prompt"
date: 2017-04-14
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2017-04-14
Running Windows 10 and Ubuntu on an old Acer 5620 laptop. I've been running both on it for years. I did a fresh install of 17.04 over my 16.10. Now when I try to boot into Ubuntu, it hangs with the grub> prompt. How do I get Ubuntu to load?

I like to do fresh installs, but the last few releases of Ubuntu have given me grief, both on my laptop and my desktop. As I recall, 16.10 also sent me to the grub> prompt. I had to reinstall 16.04 LTS and then upgrade to 16.10.

I built the desktop around MSI X58 Pro-E motherboard and Nvidia GeForce GT 220 graphics. I want to figure out how to fix my laptop before tackling the desktop because I use the desktop for my serious work.

---

### Post by yancek on 2017-04-14
Were you using UEFI with your windows and old Ubuntu?  Best to see the details.  If you can't boot the installed Ubuntu, boot the installation DVD/flash drive and go to the site below and download the boot repair software as instructed on that page.  If you select the Create BootInfo Summary option, when it finishes it will give you a link which you can post here and that will have enough details for someone to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rplantz on 2017-04-15
Thank you, yancek. I ran Boot-Repair, which generated [http://paste2.org/Cjv3ywmh]("http://paste2.org/Cjv3ywmh")

---

### Post by oldfred on 2017-04-15
You have BIOS/MBR installs.
But it looks like you installed grub to a partition which means it can not be used to boot except by third party tools that suggest installing grub to partition.
But grub says never to install to a partition as then it is forced to use blocklists which are fragile. And then you blame Linux for a third party Windows tool problem when grub does not work.

BIOS systems only boot from drive's MBR. So you have to install grub to  a drive like sda, not to a partition like sda5.
Boot-Repair can reinstall grub to MBR.

---

### Post by rplantz on 2017-04-15
Thank you, oldfred, for taking the time to look at this.

I want to maintain the Windows bootloader because it offers many tools for debugging Windows issues, which grub does not. I have been using the technique of installing grub to a partition since Windows 8 came out in August 2012, and it has always worked just fine. I do realize that Microsoft has made this inconvenient, and that Ubuntu is one of the few (the only?) distros that allow this set up. Perhaps Ubuntu has changed this for 17.04.

To be clear, I'm not trying to place "blame" here. I fully appreciate the volunteer work that goes into all Linux distros, and it would be wrong of me to complain about anything that does not suit me. I am simply trying to determine if I'm doing something wrong, or if I need to change the way I do things.

And there is the possibility that the Ubuntu maintainers did not intend to make whatever change is causing my problems, in which case they would want to know about it. I volunteer a fair amount of time to create things to help others ([http://bob.cs.sonoma.edu]("http://bob.cs.sonoma.edu")), and I appreciate any feedback that helps me to improve my work.

---

### Post by rplantz on 2017-04-15
Another piece of information here. When I boot into the [FONT=Courier New]grub>[/FONT] prompt, the [FONT=Courier New]ls[/FONT] command gives me "[FONT=Courier New]Error 14: Filesystem compatibility error, cannot read whole file[/FONT]"

---

### Post by oldfred on 2017-04-15
Grub2 does not use error codes. That was last used with grub legacy.

If using Neosmart, it uses the ancient grub4dos which is based on grub legacy, so error is probably from grub4dos.
Lost link to old error codes (he stopped posting those pages as so obsolete) and do not know what error 14 is.
Found another source.
[https://www.gnu.org/software/grub/manual/legacy/grub.html#Troubleshooting](https://www.gnu.org/software/grub/manual/legacy/grub.html#Troubleshooting)
> 14 : Filesystem compatibility error, cannot read whole file
Some of the filesystem reading code in GRUB has limits on the length of the files it can read. This error is returned when the user runs into such a limit.       



 [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Some old BIOS or BIOS settings if not AHCI may cause grub boot issues if boot files or grub files are beyond an very old BIOS limit of 137GB. Where on drive are boot files. Some have not had issue as files were located inside 137 even if partition went past 137, but then update put new files beyond limit.

---

### Post by rplantz on 2017-04-16
> **oldfred said:**
> 
Some old BIOS or BIOS settings if not AHCI may cause grub boot issues if boot files or grub files are beyond an very old BIOS limit of 137GB. Where on drive are boot files. Some have not had issue as files were located inside 137 even if partition went past 137, but then update put new files beyond limit.

This should not be the problem I'm having since the entire root partition ('/' is withing the first 110 GB of the disk. My '/home' partition comes after that.

I guess I'll try installing 16.04 and then updating that to 17.04. I think that's what I ended up doing when I went from 16.04 to 16.10. Sigh.

---

### Post by rplantz on 2017-04-17
I did a fresh 17.04 install by first doing a fresh 16.04 LTS install. It would not allow me to update directly to 17.04. I had to do 16.10 then 17.04. As I recall, I had to do this when I went from 16.04 to 16.10. Aside from taking a long time, all went well. Must be some sort of problem with the installer on older machines. I've done my laptop, a several year old Acer 5620. Next I will do my home built desktop, which is also several years old. Both machines use BIOS.

---

