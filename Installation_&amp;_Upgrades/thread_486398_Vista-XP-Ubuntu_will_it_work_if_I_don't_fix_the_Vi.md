---
title: "Vista-XP-Ubuntu: will it work if I don't fix the Vista/XP booting first?"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by kaltv on 2007-06-28
Here's the situation: I have this Lenovo Thinkpad at work, which quite unfortunately came loaded with Vista, which turned out to barely work with some of the office equipment, when XP (on other laptops) does work. So obviously, I thought of installing XP  on it (with perhaps Ubuntu thrown in the mix like my home laptop :P ).

After much headaches (upon which I learned that most Vista defrag programs "don't bother" moving all your files to the beginning of the disk anymore), I resized the Vista partition.

Now here's the problem: this particular laptop was purchased in another city. And the install CD was apparently left there. And nobody knows where it is anyway.

Current tri-boot tutorials recommend "fixing" the boot manager right after installing XP, but unfortunately I don't have that CD at hand. 

So here's the question: if I install XP, then install Ubuntu 7.04 immediately after, will Ubuntu fix the problem by recognizing both Vista and XP anyway? Will XP's boot manager's inability to recognize Vista hamper Ubuntu's ability to do so? If not, is there a way for me to force recognition?

Thanks!

---

### Post by lord bacon on 2007-06-28
hmm if i remember correctly, i tried somethin similar on my laptop.. with bad results.. if you install XP then as long as u can boot into it, when u install Ubuntu GRUB should recognise the boot loader and let u boot into XP, as for being able to boot into vista and XP, i failed to do it and in the end got annoyed and just had a vista install then an ubuntu install, i am going to be removing vista next week (when im on hols) and putting XP on with ubuntu, if i feel enthused i will be trying to get the tripleboot arrangement, but anyways back to you question, if you can get XP and vista to dual boot first, then when u install GRUB it should pick up the loader (which ever one it is that u will use to get XP and VIsta to boot) and then on boot u will be given the GRUB menu follew by the windows menu listing which Windows OS u want to use..

if you can stand to lose the data on there (or have it backed up) i would recommend getting a copy of the vistakey, then drop into your local PC store and see if u can borrow a vista CD for the afternoon (your key should work with any CD) then completelywipe your HDD and start from scratch..

hope this helps..
Lord Bacon

---

### Post by Pumalite on 2007-06-28
Check this too:

[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

