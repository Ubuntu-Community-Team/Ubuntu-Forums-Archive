---
title: "dual boot lubuntu on Chromebook 2, partition header problem"
date: 2016-04-13
forum: Installation &amp; Upgrades
---

### Post by Ivo_Degn on 2016-04-13
hey all,
I have a Chromebook 2 (Toshiba). After a couple of days of playing around with Chrome OS I decided I wanted at least dual boot. 

I followed these instructions: [http://chromeos-cr48.blogspot.de/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.de/2013/05/chrubuntu-one-script-to-rule-them-all_31.html) to install lubuntu LTS. All went well, except that at rebooting, the laptop rebooted into Chrome OS. 
Researching I found these instructions: [https://sites.google.com/site/chromeoswikisite/home/what-s-new-in-dev-and-beta/developer-mode](https://sites.google.com/site/chromeoswikisite/home/what-s-new-in-dev-and-beta/developer-mode) and added the script that would allow me to boot into ubuntu. 
One difficulty was that the partition seem to be named differently than described. /dev/sda couldn't be found. Using rootdev, I found it's /dev/dm-0, so I exchanged that.

Now, obviously I'm still rather green. I'm not sure if the partition I want in the script is the one that rootdev shows.
Either way, what happens is that; if I type "ubuntu" in the developer console, it gives the following error:
"WARNING: Primary GPT header is invalid
WARNING: Secondray GPT header is invalid
ERROR: GptSanityCheck() returned 4: GPT_ERROR_INVALID_SECTOR_SIZE"

I'm guessing something went wrong in the installation since it didn't boot into Ubuntu in the first place. The other possibility is that I gave it the wrong partition to boot Ubuntu from. Or something else entirely?
Would appreciate any help.

Cheers!
Ivo

---

### Post by TheFu on 2016-04-13
Which model of toshiba 2 do you have?  There are different instructions for all 6 of them.
For the "C" series: [https://github.com/brendenyule/NativeToshibaCB2Guide](https://github.com/brendenyule/NativeToshibaCB2Guide)
For the "B" series: [http://www.fascinatingcaptain.com/howto/install-ubuntu-on-the-toshiba-chromebook-2-in-5-steps/](http://www.fascinatingcaptain.com/howto/install-ubuntu-on-the-toshiba-chromebook-2-in-5-steps/)
Don't know "A" series. Sorry.

I've not gotten whole disk encryption working, so run using crouton with encryption currently: [https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)
I have a CB35-C3350 - Ubuntu loads, but because it doesn't have whole drive encryption, I wiped it. That isn't useful to me - a portable device without whole drive encryption.

---

### Post by Ivo_Degn on 2016-04-13
Hey TheFu,
thanks for your response. If I get those instructions right, they are for wiping chrome OS completely and substituting it with Linux. That is quite tempting, but I'm not there yet. 
I didn't know there were different models of the toshiba 2. Don't know how to find out which model I'm on - do you know?

edit: recovery says SWANKY. Is that the version?

---

### Post by TheFu on 2016-04-13
> **Ivo_Degn said:**
> I didn't know there were different models of the toshiba 2. Don't know how to find out which model I'm on - do you know?

My model, as stated above, is CB35-C3350.  Perhaps you could check the box for something like that?

The 'C' comes just after the '-' and before the 3350.

There is also the CPU. I think every different model has a different CPU.  /proc/cpuinfo

---

### Post by Ivo_Degn on 2016-04-13
edit: found it. It's B.

Do I also have to follow other instructions if I want to dual boot?

---

