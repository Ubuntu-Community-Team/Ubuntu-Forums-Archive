---
title: "Loss of sound when coming off 'standby' Mint 17.3"
date: 2017-09-18
forum: MINT
---

### Post by J Tinsby on 2017-09-18
I sincerely apologize if I have posted this problem before, a search didn't show it.

Your are my last best hope in solving a problem that has plagued me since I installed Mint, now I am at version 17.3 and the problem remains. There's nothing wrong with not knowing, I don't know! But gee someone must have a suggestion at least. Weeks back I changed the kernel to a newer one, it did nothing to the original problem but cause me more grief so I am back to the original one.

 I did find a similar almost identical problem going back to My 31 of 2010: [https://ubuntuforums.org/showthread.php?t=1498259](https://ubuntuforums.org/showthread.php?t=1498259) But that was Ubuntu and I have Mint.

I have the same Supreme FX-Xfi sound card as the OP did  / does. My sound will disappear almost every time when I wake the machine from the standby mode. To get it back I have to type in :

```
sudo alsa force-reload 
```

Then restart Firefox and I have sound again..... until I put it on standby walk away then come back  and resume operating.

My computer is dual boot W7 and Mint, an ASUS Rampage Extreme MOBO, with Grub now installed on /dev/sda so it's booting both 7 and Mint, it wasn't that way until I made the kernel change.

Bringing up the alsa mixer shows me the choices of soundcards, it is set on the default one the other ones are 0 HDA Intel and 1 HDA Nvidia ( but there is no sound driver installed on the Nvidia graphics card ) needless to say only the default one works at all.

Can anyone please give me some idea as to what to do? the novelty of having to use the terminal each time to re-intialize the sound is wearing thin :( I don't want to blindly edit files without some direction, I am a Mint* user* not a guru ;)

Thank you all very much for reading this and maybe someone has some ideas.

Regards,

J Tinsby

---

