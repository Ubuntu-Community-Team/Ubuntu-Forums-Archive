---
title: "No boot"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by Valdemar_Karlsson on 2013-08-19
I cant get ubuntu-13.04-desktop-amd64 to boot.
It runs well from usb and installs with no problems.
I tried on single disk and multiple disk. 


Tried Boot-Repair and it seemed to work but the result are still the same.

The url I got was [http://paste.ubuntu.com/6003862](http://paste.ubuntu.com/6003862)  
 
I have motherboard X58A-UDR3 from GIGABYTE ant intel i7 12 GB ram.

Wath to do ??  

Valle.

---

### Post by oldfred on 2013-08-19
When you say it does not boot do you just get black screen? With one install you do not get grub menu normally as it knows what you want to boot. If you hold shift from BIOS do you get grub menu.
Some with newer UEFI based motherboard have found escape works instead of shift?

What video card/chip are you using?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by Valdemar_Karlsson on 2013-08-20
Tanks for helping.
Grub 2 booting fine from sdc1.
Selecting Ubuntu (normal boot) and just got an empty screen.
When I start in safe mode it ends up with kernel panic. It seems like it newer mounts sdc1 and cant load [COLOR=#000000]/boot/grub/i386-pc/core.img
Problem are it crashes before it could write any logs.. [/COLOR]

---

### Post by Valdemar_Karlsson on 2013-08-20
[COLOR=#000000]When booting in recovery mode it puts out a lot of text and when it stops I could see one big problem..[/COLOR]

[COLOR=#000000]mount: mounting /dev/sdc1 on /root faild

(the cernal panic was not correct above)
[/COLOR]

---

### Post by oldfred on 2013-08-20
You could try fsck, or just a re-install.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdc1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdc1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdc1

---

### Post by Valdemar_Karlsson on 2013-08-20
Thanks for helpin olfred.
When using liveCD there are no problem mount the disk.
Also run the [COLOR=#000000]e2fsck without problems. I tried to install several times on different drives. Unconnected so theres only one disk and always the same result.[/COLOR]
I installed lubuntu 32 bit version and that works directly.
Here are the screen after tryning to boot in recovery mode:   [https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-prn2/1167555_621323664554932_1795976417_o.jpg](https://fbcdn-sphotos-d-a.akamaihd.net/hphotos-ak-prn2/1167555_621323664554932_1795976417_o.jpg)

---

### Post by oldfred on 2013-08-20
I now notice you used ext2 for root. I would try ext4.

Also some BIOS have issues with very large / (root) partitions. Either a separate /boot or make a 25GB / and make rest of drive /home.

---

### Post by Valdemar_Karlsson on 2013-08-21
Finally its booting :-) I read this post [http://ubuntuforums.org/showthread.php?t=1373394](http://ubuntuforums.org/showthread.php?t=1373394) and found **[COLOR=#000000][meierfra.]("http://ubuntuforums.org/member.php?u=552151") [/COLOR]**[COLOR=#000000]saying:
Grub always considers the boot drive as "(hd0)". So the correct entry for root will always be: [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]set root=(hd0,1)[/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]And change the load of [/COLOR][COLOR=#000000]vmlinuz to use UUID to use the correct disk[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]linux    /vmlinuz root=UUID=fd0c6442-dc3d-49ba-8e46-91657460fe52[/COLOR]

[COLOR=#000000]So by by pressing e in grub menu I could edit these rows:[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd2,msdos1'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd2,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd2,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci2,msdos1  8eacbd4f-d612-4ece-b417-4417fbb63fc2
    [COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 8eacbd4f-d612-4ece-b417-4417fbb63fc2
    [COLOR=#AA22FF]**fi**[/COLOR]
linux    /boot/vmlinuz-3.8.0-19-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR]/dev/sdc1 ro persistent  quiet splash [COLOR=#B8860B]$vt_handoff
[/COLOR][COLOR=#000000]
to 
[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]linux    /boot/vmlinuz-3.8.0-19-generic [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=UUID=[/COLOR][COLOR=#000000][FONT=Verdana]8eacbd4f-d612-4ece-b417-4417fbb63fc2[/FONT][/COLOR][COLOR=#000000][FONT=Verdana] ro persistent  quiet splash [/FONT][/COLOR][COLOR=#B8860B][FONT=Verdana]$vt_handoff
[/FONT][/COLOR][FONT=Verdana][COLOR=#000000]
[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]Press F10 and its boots like a dream :-)  (very fast also with the SSD disk)
[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]
[/COLOR][/FONT][FONT=Verdana][COLOR=#000000]What is this mess?? Why isn't UUID used every where ?? I spend lots of hours on this silly problem...

But now the mouse and network does not work.. But I hope to solve this, now there should be logfiles to check... (But ubuntu isn't where easy to handle without the mouse) 
[/COLOR][/FONT][COLOR=#B8860B][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by oldfred on 2013-08-21
IF a thread from meirerfia. it is old, but still useful. 
But the search by UUID is supposed to override the set root. Or in your case the search must not have been working?
I have had similar issues with installs to flash drives where order changes a lot, but with 4 hard drives I have not had that issue, but I normally install grub2's boot loader to the MBR of the same drive I boot from for reliability. Then only that drive has to work to boot. But then my settings are always hd0.

I normally boot 12.04, but my Raring install does use UUID in the linux line by default, but it has been updated a couple of times. But I cannot use any device settings as I skipped a port in motherboard. Sometimes  flash drive is sde and on reboot it becomes sdb renumbering all my other higher letter drive that I use more.

---

### Post by Valdemar_Karlsson on 2013-08-21
And from terminal I just run:
 sudo [FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif]update-grub
 
and grub.cfg file was updated correctly and now its boots ok... [/FONT]

---

