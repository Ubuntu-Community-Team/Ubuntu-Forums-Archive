---
title: "Dualboot windows 7 problem"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by Lablabla on 2011-10-26
Hi,
I'm stating university and need to install Linux on my laptop,
I wanted to dualboot with Windows 7. I followed this guide:
[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/")
it installed and restateed. after that I installed easyBCD and added the ubuntu entry and restarted.

in the Windows boot loader which pops up after restart I select linux and it starts GRUB4DOS.
tried reinstalling several times with some different settings, same result always.

Only thing I didn't try is to format the entire HD and installing  linux alone. Do wish to avoid this :-)

Any help would be appreciated!
Carmel

---

### Post by oldfred on 2011-10-26
Welcome to the forums.

Where are you getting grub4dos? If you followed the instructions it should be grub that easyBCD is loading from the /boot partition.

To see where everything is installed.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Lablabla on 2011-10-26
This script is for linux, my problem is I can't load into linux. at all.

after installing it, when selecting Ubuntu from the boot loader, it launches this GRUB4DOS.

The only way I can load Ubuntu is this live option, or what ever it's called.

is that what you ment?

Thanks for the reply!
Carmel

P.s, I don't know which partition should be selected when installing (in the guide it's /boot). I tried installing to /boot, as well as to the root / partition. both didn't work.

Now I see that the Format check box on the /boot partition is selected. don't know how crucial this is, but I'm gonna give it another go. about the 5th or more time today.
will report soon.

Edit 2:
Didn't work yet. Don't know if it matters, but I'm installing unbuntu 11.10, not 11.04 like the guide says. I downloaded it yesterday.

---

### Post by oldfred on 2011-10-26
My only complaint with the link you have is the recommendation for a separate /boot. For most desktops is not not required. Some old systems or servers with RAID or LVM may need a separate /boot.

---

### Post by Lablabla on 2011-10-26
I tried both ways, as he recommended and using the default boot.

in the easyBCD. the linux entry shoutld point to BOOT?
because when so, i'm getting a whole different Windows 7 Error on the boot loader.

i've got one more idea for the instlalation.


what is this GRUB4DOS for anyway?
Is there a way to load ubuntu from it?

Thanks again.

---

### Post by oldfred on 2011-10-26
Grub4dos is the windows version of grub. I have not used it.

---

