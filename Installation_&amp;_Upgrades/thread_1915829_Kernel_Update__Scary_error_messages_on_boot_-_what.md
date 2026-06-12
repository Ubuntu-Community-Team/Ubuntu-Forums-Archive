---
title: "Kernel Update:  Scary error messages on boot - what next?"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by Redflea on 2012-01-27
I was having wifi problems (very slow performance) so I decided to try upgrading the kernel.  

Since I'm a Linux noob, I looked for a simple approach and found this:

[http://www.ramoonus.nl/2011/05/19/linux-kernel-2-6-39-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/05/19/linux-kernel-2-6-39-installation-guide-for-ubuntu-linux/)

Used that to upgrade the kernel to:

2.6.39-020639-generic

Rebooted, selected that kernel, and after a couple scary error messages things booted fine and wifi internet is SCREAMING fast. 

Assuming nothing significant is borked w/the new kernel install, I AM HAPPY!   

So based on the error messages (see attached picture), how much do I need to worry?

Any advice on an alternate 2.6.39-020639-generic kernel install process that might clean up error messages?

---

### Post by varunendra on 2012-01-27
To me, both of those messages ("*Driver 'mdio-gpio' is already registered, aborting....*" and "*..thermal reporting for required devices not enabled, aborting.*") seem harmless, and a quick search suggests that they are perhaps commonly associated with custom built kernels which have certain kind of supports not enabled during compilation (mistakenly or intentionally).

You may check your /etc/modules file to see if it has an entry for mdio-gpio module, as suggested in this thread:
[http://www.linuxquestions.org/questions/linux-newbie-8/a-small-error-of-booting-on-kernel-3-0-0-a-895373/](http://www.linuxquestions.org/questions/linux-newbie-8/a-small-error-of-booting-on-kernel-3-0-0-a-895373/)
Comment it out (or delete the line) if there is.

Although both of these seem harmless, they seem to disappear with a kernel upgrade. Accordingly, you may try installing a newer (backported) kernel from [here]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa"). But if everything is working fine despite those messages, I'd say just leave it since backported kernels may sometimes cause stability problems with some systems.
(the description of the ppa I linked above has this to say- "[COLOR=DarkSlateGray]*The quality of these packages is such that you had better know what  you're doing. Don't come crying to the kernel team if it kills all of  your kittens."*[/COLOR] ;))

Also, have you tried a live cd of 11.10 on your system? It comes with the newer kernel by default and thus may support your system better.


**Bottomline: **They seem harmless. So just leave it as it is as long as you don't notice any problems due to it. Better try 11.10 or wait for 12.04 LTS instead of taking pain in fixing it.

---

### Post by Redflea on 2012-01-27
> **varunendra said:**
> To me, both of those messages ("*Driver 'mdio-gpio' is already registered, aborting....*" and "*..thermal reporting for required devices not enabled, aborting.*") seem harmless, and a quick search suggests that they are perhaps commonly associated with custom built kernels which have certain kind of supports not enabled during compilation (mistakenly or intentionally).

You may check your /etc/modules file to see if it has an entry for mdio-gpio module, as suggested in this thread:
[http://www.linuxquestions.org/questions/linux-newbie-8/a-small-error-of-booting-on-kernel-3-0-0-a-895373/](http://www.linuxquestions.org/questions/linux-newbie-8/a-small-error-of-booting-on-kernel-3-0-0-a-895373/)
Comment it out (or delete the line) if there is.

Although both of these seem harmless, they seem to disappear with a kernel upgrade. Accordingly, you may try installing a newer (backported) kernel from [here]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa"). But if everything is working fine despite those messages, I'd say just leave it since backported kernels may sometimes cause stability problems with some systems.
(the description of the ppa I linked above has this to say- "[COLOR=DarkSlateGray]*The quality of these packages is such that you had better know what  you're doing. Don't come crying to the kernel team if it kills all of  your kittens."*[/COLOR] ;))

Also, have you tried a live cd of 11.10 on your system? It comes with the newer kernel by default and thus may support your system better.


**Bottomline: **They seem harmless. So just leave it as it is as long as you don't notice any problems due to it. Better try 11.10 or wait for 12.04 LTS instead of taking pain in fixing it.

I think I owe you a thanks for your help here and on the original wifi speed thread.   :) 

I'm using the system primarily to build Android for my Touchpad, and that is working flawlessly right now, so I think I'll wait for 12.04 LTS...plus, though I don't have any kittens, we do have a very cute chihuahua which I call our "cat-dog", and I wouldn't want it to be mistaken for a kitty. ;-)

---

### Post by varunendra on 2012-01-27
> **Redflea said:**
> I think I owe you a thanks for your help here and on the original wifi speed thread
Wow! You got me thinking..:-k

I'm trying very hard to find that post or the line that could have helped you,.. but.. all I can find is just comments on your already solved problems :)

So - Thanks for the free 'Thank-You' :D

As for the *"kitten"* warning on the ppa, I have very recently personally experienced that with a backported kernel on 10.04.3.

I needed Intel HD graphics support which was not natively supported in 10.04.3. So installed a (reputed) backported kernel. Everything started working great until I pressed 'Alt+tab'. It crashed the system everytime I pressed Alt+tab. Found that it was a known bug with that "graphics + kernel" combination, fixing which was too much pain. So I tried 11.10 instead on the laptop and everything worked wonderfully with it.

That said, the backported kernel/modules are usually known for better performance and thus are even encouraged by some experts (even Linus Torvalds himself supports the idea of 'Backporting'). So my case maybe one of a few exceptions. But with the experience I've had, I'd always recommend to first try finding a distro that works 'out-of-box', and use a backported kernel/module only as the last resort, or if it is guaranteed to work without breaking things.

[COLOR=DarkSlateGray]*(Phew..! Now I think I can rightfully except that thank-you of yours.., still not for any help though, but for the long lectures I made ;))*[/COLOR]

---

