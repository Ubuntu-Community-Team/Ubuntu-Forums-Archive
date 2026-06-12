---
title: "Where's Windows XP after Dual-Boot Install?"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by suttles95 on 2007-12-16
I just followed the instructions on [www.psychocats.net/ubuntu/installing](www.psychocats.net/ubuntu/installing) for installing Ubuntu as a dual-boot with Windows XP which I already had on my computer.

It went through the initial steps, and I selected the first option for installation as requested so that it would install it as a dual-boot. I then entered my username and password, but it never started the migration wizard to help bring my stuff over from Windows.

How can I tell if Windows is on there? I go to Places--Computer, and I see two icons: CD-RW/DVD-ROM Drive and File System.

Can anyone help me?

I did back-up everything in My Documents onto 5 different CD-RWs. So just in case Windows is toast, I can reinstall everything from there into Ubuntu, right? But I'd really rather be able to access Windows.

Also, how do I change the resolution size so that the entire message box appears on my screen (the enter button is too low down).

Someone on Launchpad instructed me to run blkid and see the results.  Here's what I got:

/dev/hda1: UUID="4bae071b-3094-4622-a999-56425a722d76" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: TYPE="swap" UUID="66480eb1-9034-4f6c-83d0-c272eae6bb43".

Can someone please help from here?

---

### Post by mikewhatever on 2007-12-16
> /dev/hda1: UUID="4bae071b-3094-4622-a999-56425a722d76" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: TYPE="swap" UUID="66480eb1-9034-4f6c-83d0-c272eae6bb43".


If those are the only partitions on the HDD, you have formatted Windows. Just to verify that, can you post the output of <sudo fdisk -lu>.

---

### Post by logos34 on 2007-12-16
Sounds like you accidently selected the next radio button down 'Guided - use entire disk', not 'Guided - resize...'.  One little slip is all it takes.

Blkid should at the very least be showing xp as 'TYPE=ntfs'...To tell for sure run
[B]
sudo fdisk -l[/B]

If windows is history, probably the best thing to do is reinstall everything, xp first.  You COULD shrink ubuntu root down and reinstall windows right after it, but you'll have to reinstall grub because windows will write it's own bootloader to the mbr (no way to prevent it).  Then again, there's a possiblity windows will give you problems booting in that postition.
So reinstalling everything is my advice.

(You can also use gparted (0.3.4.) to shrink ubuntu root from the left (to right), clearing a space at the front of the disk, but that tales as long if not longer than just reinstalling everything.)

---

