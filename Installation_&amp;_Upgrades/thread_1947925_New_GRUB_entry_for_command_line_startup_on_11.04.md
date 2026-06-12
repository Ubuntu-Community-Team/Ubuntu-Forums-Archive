---
title: "New GRUB entry for command line startup on 11.04"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by rafael_a on 2012-03-27
Hello,
I have Ubuntu 11.04 full (with Gnome) installed on my virtualbox. I use it to download torrents, and wanted to be able to start it on command line too. So I wanted to have 2 entries on GRUB, 1 for command line, and other for Gnome. Is that possible?
I searched the forum and google, and only solutions for starting on command line. I know I can type 'startx' and start Gnome, but I really wanted to have 2 entries on GRUB.

Thanks in advance!

---

### Post by oldfred on 2012-03-27
Copy your grub2 boot stanza into 40_custom and add "text" after quiet & splash

quiet splash text

Copy boot stanza from this:
gedit /boot/grub/grub.cfg
Copy them to and edit to add text:
gksu gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by rafael_a on 2012-03-29
Gotcha!
Did that and it seemed to work, but I get stuck on "Checking battery state...".
Been checking other threads, and it seems to be a poblem with the power manager service. Thought that would not be necessary, since I'm using the OS inside a virtual machine on Virtual Box, but using BUM (boot up manager) I could see that the app is responsable for the hotkeys too. I'm afraid of screwing something, and not be able to boot at all after that. Maybe I should leave it alone.
But thanks a lot oldfred!

---

### Post by oldfred on 2012-03-29
I see a lot of users posting the checking battery state, but that just seems to be what is posted last and it is something else. Some systems require other parameters. Either do a search based on Ubuntu and your motherboard or system or experiment with boot parameters. Again not sure if vm changes anything or not.

nomodeset is for video, but has discussion on other parameters

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some systems also do not have default BIOS settings that work well. You may want to review. Generally Large or LBA not IDE and often best with AHCI but if booting with Windows you have to install the AHCI drivers before rebooting with AHCI on.

---

### Post by rafael_a on 2012-03-29
Thanks, I'll try that. In the mean time, there are some new observations.
I created a new line on Grub menu, the exact copy from the one generated from the kernel, which I use to start ubuntu with Gnome. I put that on the 40_custom file, and changed the "quiet splash" to "text" and ran update-grub command. So I ended up with this on /etc/grub.d/grub.cfg:

menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 7cf6df1d-1b0c-4b20-b5fd-48c8ce799c80
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=7cf6df1d-1b0c-4b20-b5fd-48c8ce799c80 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}
......
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (text)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 7cf6df1d-1b0c-4b20-b5fd-48c8ce799c80
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=7cf6df1d-1b0c-4b20-b5fd-48c8ce799c80 ro  text vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}

The lines are the same, except for the description and the "quiet splash", that was changed to "text".

The odd thing is that the error happens only on the last item, the one I created. If I change /etc/default/grub file to this:
GRUB_CMDLINE_LINUX_DEFAULT="text"
I am able to boot to command line just fine, using the 1st option on Grub (the option I used previously to access Gnome). That is weird.

Any idea why that's happening?

---

### Post by oldfred on 2012-03-29
The grub parameter file should be just updating your grub entry like you were updating manually the one entry. But manual updates are sensitive to spaces at end of line or other typo type issues. 
As posted you have part of the linux line on the next line, I assume that is actually one line.

---

