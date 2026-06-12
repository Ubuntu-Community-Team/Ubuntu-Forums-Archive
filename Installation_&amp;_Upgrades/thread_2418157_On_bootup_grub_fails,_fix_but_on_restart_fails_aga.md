---
title: "On bootup grub fails, fix but on restart fails again - include pastebin boot repair"
date: 2019-05-02
forum: Installation &amp; Upgrades
---

### Post by grumpybeard on 2019-05-02
Hi,

On PC start get boot error and can go into grub repair.

Can fix according to guide in video. Note that when I first type SET it lists a different a partition set as the prefix (hd0,gpt3 iirc), buit only setting hd0,gpt2 gets me back into a working grub and into Ubuntu. So perhaps the set to hd0,gpt2 is not sticking? or needs rebuilt?

[https://www.youtube.com/watch?v=OJTGpvZO8Oc&t=308s](https://www.youtube.com/watch?v=OJTGpvZO8Oc&t=308s)

Which then starts up grub menu and I can select Ubunto.

However on every restart the same boot fail happens, so I have to go through the grub repair steps again as per Youtube vid.

I installed then ran boot-repair, with out put posted here:

[http://paste.ubuntu.com/p/BwXtKjwk4w/](http://paste.ubuntu.com/p/BwXtKjwk4w/)



Most grateful for help as I need to complete a Uni assignment in Ubunto in a few days. Thanks!!!

---

### Post by grumpybeard on 2019-05-02
Looking at the pastebin from boot-repair, it shows it's looking for grub on gpt3, but it should be lookming on gpt2 (which I set after following instructions from youtube video and which gets me back into grub and Ubuntu)

Grateful for help on how I can change from gpt3 to gpt2 and make it stick, thanks!

Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 
    275620360 of the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this 
    location and looks [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],gpt3[COLOR=#666666])[/COLOR]/boot/grub. It also embeds following 
    components:

---

### Post by grumpybeard on 2019-05-02
below is what I do to fix on boot after grub goes into rescue shell. So how to make hd0,gpt2 stick?

grub rescue> set prefix=(hd0,gpt2)/boot/grub
grub rescue> insmod normal
grub rescue> normal

---

### Post by oldfred on 2019-05-02
Issue really is that with gpt grub needs a bios_grub partition to correctly install.
See line 1273 in report.

Shrink either partition by 2 or 3MB and create a new 1 or 2MB unformatted partition with the bios_grub flag.
Then do a full reinstall of grub to gpt's protective MBR (not just the update-grub).

---

### Post by jeremy31 on 2019-05-02
Was there ever a third partition on /dev/sda

---

### Post by grumpybeard on 2019-05-02
@jeremy31 - you'd make a good detective! Yes there was. I was originally doing my machine learning/python stuff via a VM hosted in windows 10. Today I decided Im convinced enough with my Ubuntu full dedicated install that I didnt need my Linux VMs any more so blew that partition away. I really didnt think that blowing this partition away, which was only ever used in Windows, would cause this trouble.  My next challenge is how to re-allocate the now spare ~120Gb to my current Linux partition. I believe I can do this with gparted but not when I am running Linux, so probs with a Live USB version of Ubunto or gparted iso?  Anyway, thanks very much for checking in on this thread and your willingness to help, much appreciated.

@oldfred - following your guidance, all sorted, thank-you so so much. Tested with a restart and all good, grub showing each time now. You are a :KS , have a great day

---

