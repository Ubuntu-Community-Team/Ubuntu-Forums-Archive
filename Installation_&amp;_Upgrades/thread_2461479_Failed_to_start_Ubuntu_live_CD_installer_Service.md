---
title: "Failed to start Ubuntu live CD installer Service"
date: 2021-05-01
forum: Installation &amp; Upgrades
---

### Post by Acharn on 2021-05-01
I've installed several Ubuntu versions on USB digital drives to experiment. I just finished updating the 20.04 LTS installation and the 20.10 installation. The procedure is pretty easy, except the Ubuntu installer requires setting up two partitions, one for the BIOS boot loader and one the EFI data, and doesn't tell you how large they must be to work.

So I downloaded the 21.04 Hirsute Hippo .iso and burned it to disk. When I tried to boot, I selected Ubuntu from the menu and after a minute or so my screen was showing the motherboard's logo, the rotating thingy, and the name Ubuntu. That lasted for 4:00 minutes, then the screen went blank and then came back without the rotating thingy. At 5:00 minutes that went away and I got a checklist. The first item was in red and said "[FAILED] unmounting /cdrom." Then it showed about 25 entries, all preceded by "[OK]" and stopped for about another minute and displayed, "[FAILED] Failed to start Ubuntu live CD installer Service...el crash signatures..."

My CPU is an AMD A10-5800K. I had a problem a few years ago when a change to X had an obscure bug that only seemed to affect this particular CPU, but then the screen just went blank, and Ubuntu fixed the problem two releases later. I haven't seen any other posts saying the live CD failed to boot, so I don't know what to do next. I'm not including much info about my system because I don't know what might be useful, but I will give it if wanted. I thought about downloading the 21.10 daily, but the browser says it would take three hours, so I don't want to go there yet. Oh, the motherboard is seven years old, so the EFI might be a problem according to a post I saw about Kubuntu.

---

### Post by yancek on 2021-05-01
Did you verify the download of the iso from the Ubuntu site before you burned it to a DVD (or wrote to a usb)??

You indicate you are doing an "update" of 20.04 and 20.10 which would indicate both are already installed.  Don't see how you could be having the problems you mention on updating?

On installed systems, you eihter have a 1-2MB unformatted bios_grub partition or an EFI partition formatted FAT32.  Don't need both.

It isn't really clear to me from your post is you have Ubuntu installed and are updating or if you are trying to install the different versions on your hard drive or if you are trying to multiboot 'live' systems on a flash drive so could you clarify?

---

### Post by Acharn on 2021-05-03
Sorry for being unclear. From time to time I browse Linux distributions. I do this by installing the distribution on a USB 3.0 flash drive. I've been doing this for several years now, and don't remember why I found this method better than "persistent" live USB installations. I don't have enough space on my hard drive for a satisfactory dual install, so this is perfect for me, especially since 64GB flash drives became affordable. The procedure is explained at [How do I Install an Entire Ubuntu on a USB Flash Drive?]("https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/"). I expect eventually using Windows 7 will become untenable, but for now I have a couple of games that I can't run in Wine and won't run on Windows 10 (which I utterly detest anyway).

I was referring to booting Ubuntu from USB and updating, in the same way I would update an Ubuntu install on my hard drive. I was able to boot up both the 20.04 LTS and the 20.10 drives. Then I wanted to try the newly released 21.04, Hirsute Hippo. No, I didn't verify the download -- I don't have gpg on my Windows 7 desktop, and that's what I was using to download. I did, however, download another copy of the .iso and it had exactly the same problem.

I may have just stumbled on the cause of the problem, although I would think I would see more posts about people unable to boot the Live CD. Over at PC Magazine is and article dated April 27, 20021, titled [Upgrading to Ubuntu 21.04 Is Not a Good Idea Right Now]("https://www.pcmag.com/news/upgrading-to-ubuntu-2104-is-not-a-good-idea-right-now"). The article ends, "For now, if you're running Ubuntu 20.10 then the best thing to do is keep using it and wait for Canonical to give the all clear, or for the upgrade notification to appear."

---

