---
title: "(initramfs) Need  Install Help (Kubuntu v7.10)"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by Kiefer Rodriguez on 2008-01-29
Hey, My name is Kiefer Rodriguez. I'm an Australian IT Student, Currently studying for a diploma in IT (Programming & Software Dev.).

Im completely new to (K)Ubuntu and Linux alltogether, And today I recieved the following Live CD's in the mail:

-Kubuntu 32-Bit v7.10
-Kubuntu 64-Bit v7.10
-Ubuntu 32-Bit v7.10
-Ubuntu 64-Bit v7.10

I chucked the Kubuntu 32-Bit Live CD in my CD drive and reset my (Acer Travelmate 520) Laptop. 
The installer menu appears and I choose 'Install Kubuntu" and I get a loading splash screen, then a prompt like this:

(initramfs)_

As Im new to the world of Linux, Im not sure how to continue, Is there a way to continue the installation?
My PC specs are as follows:

-Pent II 800mhz
-External Monitor (The screen attached to my laptop died a while ago, I rarely use it, Hence why im installing Linux, Might be a good chance to get my hands dirty with a new OS hehe)
-Windows XP Pro SP1

Im on a rather slow wireless connection at the moment, shared with other family members, So downloading large files is not really an option for me.

Any help would be greatly appreciated, Thanks.

Kiefer.

EDIT: If ive left anything out, Dont hesitate to ask :)

---

### Post by Partyboi2 on 2008-01-29
If you have not got much ram and older hardware you may find the alternate cd's better to install with.
[ubuntu alternate cd]("http://releases.ubuntu.com/releases/7.10/")
[xubuntu alternate cd]("http://mirror.internode.on.net/pub/ubuntu/xubuntu/7.10/release/")

---

### Post by Kiefer Rodriguez on 2008-01-29
> **Partyboi2 said:**
> If you have not got much ram and older hardware you may find the alternate cd's better to install with.
[ubuntu alternate cd]("http://releases.ubuntu.com/releases/7.10/")
[xubuntu alternate cd]("http://mirror.internode.on.net/pub/ubuntu/xubuntu/7.10/release/")


Thanks for the reply, Unfortunatly I am without sufficient internet speeds or a CD/DVD Burner :(
Is there any other options that might help me out? 
Thanks,

Kiefer Rodriguez :)

---

### Post by Partyboi2 on 2008-01-29
You could have a look at a barebone install
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

On a side note where in Australia are you studying?

---

### Post by Kiefer Rodriguez on 2008-01-29
> **Partyboi2 said:**
> You could have a look at a barebone install
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

On a side note where in Australia are you studying?

Cheers, Ill Take a look.

Im studying in Adelaide City, Got mates in Melbourne thought :)

---

### Post by Partyboi2 on 2008-01-29
well hope you get ubuntu installed and all the best with your study this year :)

---

### Post by Kiefer Rodriguez on 2008-01-29
> **Partyboi2 said:**
> well hope you get ubuntu installed and all the best with your study this year :)

Thanks mate, I hope I get it installed too ^_^
I'll let you know how the barebone install goes :)

Kiefer Rodriguez

---

### Post by Kiefer Rodriguez on 2008-01-31
Hoorah! Got it to install ^_^ (Live CD, Not Barebone)

For anyone with the same problem, When the initial install menu shows, press F6 while 'Start installation' is selected to change the boot options and type 'irqpoll' and it should work :D . Can anyone collaborate on what the 'irqpoll' flag does? 

Thanks, Im now running Kubuntu 7.10, though still having issues setting up my wireless adapter to work :(


~Kiefer Rodriguez :)

---

### Post by Partyboi2 on 2008-01-31
> irqpoll:
When an interrupt is not handled search all handlers
for it. Also check all handlers each timer
interrupt. Intended to get systems with badly broken
firmware running
did you add irqpoll to grub menu.lst so that it boots with that boot option each time?

---

### Post by Kiefer Rodriguez on 2008-02-01
> **Partyboi2 said:**
> did you add irqpoll to grub menu.lst so that it boots with that boot option each time?

Ummm, (Me = Linux Noob).
All i did was, when I installed, I added the irqpoll option. Everything seems to be working A-Okay. 
Badly broken firmware? Uh-Oh? lol

Kiefer

---

### Post by Partyboi2 on 2008-02-01
When you first boot the machine and add a boot option it is only temporary for that one boot. To add it permanently so that it uses that boot option everytime you would add it to grub menu.lst located in /boot/grub directory. But in your case  it seems it was only required while booting the live cd and after the install everything was ok. So happy ubuntu-ing...

---

### Post by Kiefer Rodriguez on 2008-02-01
Cheers Mate :D
On a side note, you wouldnt be able to help me out with my wireless issue would you?
[My Wireless Issue Post]("http://ubuntuforums.org/showthread.php?t=684330")
Thanks mate.

Kiefer

---

