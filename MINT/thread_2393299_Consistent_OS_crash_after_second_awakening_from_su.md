---
title: "Consistent OS crash after second awakening from suspend."
date: 2018-06-01
forum: MINT
---

### Post by drhow2 on 2018-06-01
Please clue me if there is a better forum in which to seek help on this issue.

After a restart, I can put the machine to sleep once and it awakens properly. If I put it to sleep a second time, then it does not awaken properly. The power comes on, but the display remains black, and it is completely unresponsive to input of any sort. (Including ctrl-alt-esc and ctrl-alt-del.) I have to power down and restart. When it is in the improper power-on not-responsive state, I can tell that the processor is not idle because the fan eventually speeds up. The problem arises independently of whether or not any applications are running.

I was running the 4.10.0-38 kernel (64 bit) on an old Toshiba Satellite laptop (model L355 S7901). I had installed Linux Mint. I did not get any effective help when I posted about this in their forum. Since I imagine that whatever is causing this is at a fairly deep level not depending on the particular Ubuntu variant, I thought I would try here. Indeed, I am assuming that the issue probably involves something at the hardware driver level. In truth, I don't even have a strong preference about which distro I use on the machine. I'd be perfectly happy to try another if there is a good chance that it would help. 

I saw that there is a kernel update pending for the 4.13.0-43 version, so I decided to try that. The behavior changes, but for the worse! After only the first suspend, it awakens briefly and then spontaneously puts itself back to sleep after about 2 seconds. After that, an attempt to awaken it results in the same failure as before. (I uninstalled the newer kernel.)

I was running Vista on this machine. (I was not too worried about it since I don't keep any critical information on the machine, using it almost exclusively for browsing the web from my bedroom.) However, I decided that the time had come to switch to a decent maintained OS. I installed Mint in a dual boot configuration. Except for the problem I am reporting, I like it. However, this sleep problem is a show-stopper for me as I normally use the machine with a large flat screen TV as monitor, well across the room, and I control it with a wireless keyboard/tablet. I need to be able to put it to sleep and awaken it remotely, which is what I had been doing reliably with Vista for years. (All my configuring and testing efforts so far have been done with the laptop's display, keyboard, and tablet.)

This cannot be a hardware problem, as suspend/awaken still work perfectly when I boot Vista. I doubt that it is relevant, but the Vista OS is 32-bit. Since the AMD Turion processor supports 64-bit, I initially installed the 64-bit version of Mint. The machine has only 3GB of RAM, which should suffice for my purposes. Since 32-bit Vista still works correctly for suspend/awake, I thought maybe a 32-bit Linux might solve this problem. So I also tried the 32-bit version of Mint. Same problem.

I would very much appreciate any suggestions about how to get around the problem. It seems like it should be possible, as the software state after start up is such that suspend/awaken does work (once). It should be possible to get it back into that same state.

---

