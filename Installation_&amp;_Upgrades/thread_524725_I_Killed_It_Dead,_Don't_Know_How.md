---
title: "I Killed It Dead, Don't Know How"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by mfm3 on 2007-08-13
Hello out there,
Well, the worst has happened. Just awful. Please help me if you can. I'll start from the beginning.

I had a great-working system, Toshiba Satellite A35, I was dual booting XP Pro and Dapper. I started playing with vmware in Dapper to maybe get rid of the dual boot. It all worked great. Until Feisty. 

I wanted Firefox 2.0, Thudnerbird 2.0, etc.....things that were not easy to get with Dapper because it is "frozen" in LTS world. In hindsight, I should have stayed with Dapper and just used it. It was fine. But I wanted to stay up to date, plus it gave me something to do all day yesterday. 

So I did the "official" upgrade to edgy then to feisty, which seemed to work fine, except vmware player was broken. So I spent about 5 hours trying to get that to work, failed and gave up, and decided to just start over with Dapper this morning. I've still got the official LiveCD that came in the mail. So I told Dapper to re-format my ext3 primary linux partition and swap, leave my windows partition alone, and install Dapper on the linux partition. Ok, it trudges along, then hangs at 43% installed for about 3 hours. This is not right. System is frozen, so I killed it. cntl+alt+bkspc, never restarted after another hour, then I just powered off. I know, I know, BAD. Well it was bad. now, no matter what I do, when I power on, there's nothing. No toshiba boot screen, no bios, nothing. The machine seems to be running in that there is power on and I can hear the disk spinning. Cannot boot from CD or disk. Cannot boot anything at all. Of course this would happen......I should have just stayed with Dapper. F Feisty Fawn! 

Anyway, can anyone give me any advice? thanks.

---

### Post by kellemes on 2007-08-13
Reset bios?

---

### Post by bren on 2007-08-13
have you tried boot from livecd (feisty) to see what is left....
maybe you need to download/burn this from another computer....

bren

---

### Post by mfm3 on 2007-08-13
I cannot seem to boot from HD or from CD, screen is just black all the time.

How do I reset the BIOS?

Thanks, I'm freaking out over here....

---

### Post by fredj on 2007-08-13
Remove AC power. Remove the battery. Replace battery and AC power. Switch on.

---

### Post by mfm3 on 2007-08-14
Thank you. I did so involuntarily earlier when I took a break, and it came back on this afternoon. I then beat my head against the "wall" for awhile and Dapper is back. Woo Hoo. 

Seems like Dapper is the one for this machine.

---

### Post by madmike562 on 2007-08-14
I just finished the double upgrade myself.It does indeed break VMWare (server in my case).But your guest os folder is untouched and you can reinstall VMWare with Synaptic (all repositories enabled).Watch the terminal window in Synaptic as it will prompt you for a new serial number.
After that all is good.

---

