---
title: "ubuntu 9.10 did not remove 8.04"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by geneluck on 2010-03-06
Please could someone shed some light on this one:
I do not understand : i installed ubuntu 9.10 and deleted the 3 partitions I had installed 8.04 onto,  re-assigned them to ubuntu 9.10 . install went OK
But when I start, GRUB gives me  the choice of ubuntu 8.04? and 9.10 (on top of vista which I have on this machine also)
Can someone give me a clue why ubuntu 8.04 is still around and how I can get rid of it. I can indeed boot it OK.
When I boot 9.10 go to synaptic package manager , the only installed linux image I see is the one corresponding to 9.10!!!! I am confused.
Jean-luc

---

### Post by presence1960 on 2010-03-06
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Arkitekt on 2010-03-06
Did you do a fresh install or just update 8.04 to 9.10? if you just updated you need to go into synaptic and remove the old kernels, this will remove them from the grub list as well

---

### Post by geneluck on 2010-03-07
Thank you presence1960 and arkitekt for your responses. I had already checked for other kernels installed and it was not the problem, Thank to presence1960 suggestion, I downloaded the script and with the result file could figure out what  happened: when I installed 9.10 I deleted each linux partition in turn and re added it : (/, swap,/home) in exactly the same partitions location as before. For some reason , this caused gparted to not format these partitions and ubuntu 8.04 was still there. I then deleted all 3 , re added them ,and is time it worked ok. Thanks again

---

### Post by presence1960 on 2010-03-07
Glad you got it working, enjoy ubuntu.

---

