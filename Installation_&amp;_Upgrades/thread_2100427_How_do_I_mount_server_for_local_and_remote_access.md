---
title: "How do I mount server for local and remote access?"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by ivotkl on 2013-01-01
Okay, so it's new year. Alcohol and the following morning gave me a little idea. I want to buy a pretty powerful computer (AMD A8, 8 GB DDR3, 500 GB SATAII, 1 GB Video card) to use as a home/familiar server based at my apartment.
 
I know nothing about servers and virtualisation (if that's needed).
If virtualisation is needed, I'll read the documentation found on the sub-forum.
 
Basically, the idea is to rip all my music and movies there to allow access to family members and other computers, via SSH terminal (or a more secure one if possible). Files would be read only for everyone but me. It should also allow to upload photos inside a folder / partition and restrict allowed uploadable amount for each user. That's why I'm thinking about a partition for each user, maybe more than 1 hard drive?).
 
I wanted it to work sort of an online hosting service, but non-profitable and for my family. Maybe also have it work as a photo sharing throughout the family.
 
Oh, and by the way, only householders using Ubuntu are the ones living inside my house, so a bit of the evilness of Bill Gates might be needed.

---

### Post by darkod on 2013-01-01
1. Virtualization is not necessary, but you can use it if you want to. If you are new to servers it might be a bit too much with all the other things you will need to sort out.

2. I hope someone else will comment too, but I think the AMD A8 is too much for a server of this type. I don't know how often you will rip music, but for sharing data in the network you can use a smaller CPU. For example, my ubuntu home server is running on AMD Athlon N36L. That helps with the electrcity bill also for a server on 24/7.

3. You will probably want to use Samba shares for data sharing, and SSH only for administration of the server, not for data access. All computers can be configured to mount one or more shares on boot, and the users can use them. Configuring the permissions might be little tricky since you are new to ubuntu server, but it shouldn't be very difficult.

---

### Post by ivotkl on 2013-01-02
Darko,
Thanks a lot for the reply. Here are my answers.

1. Great. Won't use it if not necessary.

2. About A8 it was meant to be for a Gaming computer. Will definitely change it. =P

3. Thank you very much. I am not planning on putting it on 24/7, probably just while I'm using computers or upon request. I will definitely put SAMBA on it. I know that program. It allows network file sharing with Windows platform.

One more thing by the way: I would like to also allow remote access to my brother in law's PC so that I don't have to fix it over the phone or come all the way (It is around 40 Km. away and I do not have a car). Should I create a new thread for that?

---

### Post by darkod on 2013-01-02
> **ivotkl said:**
> 

One more thing by the way: I would like to also allow remote access to my brother in law's PC so that I don't have to fix it over the phone or come all the way (It is around 40 Km. away and I do not have a car). Should I create a new thread for that?

Yeah, it's best not to mix threads. If this is Ubuntu Desktop OS, I think it was easy. Don't remember the exact programs, but in the dashboard search for Remote Desktop or Remote Access and it should show up. As soon as you start typing Remote... it will show all programs that contain it.

It was very easy to allow remote access with that. You have to do it on your brothers computer of course.

---

### Post by ivotkl on 2013-01-03
Ok, so I've installed teamviewer. I am amazed. =P

One thing, how do I make it run on any-session startup? I would like to set it as default option.

Thank you.

---

### Post by ivotkl on 2013-01-07
Shameless bump and new question.

Can I add process on system startup so I do not need anyone near the PC? If so, how?

---

### Post by darkod on 2013-01-07
If it's really a daemon/service, it can usually be configured to start at boot.
If it's some manual command that you want run at boot, you can add it to /etc/rc.local before the exit 0 line. All commands there will be executed as root (so you don't need sudo in front).

If you post what you want to do, someone might have an idea.

---

### Post by ivotkl on 2013-01-07
I think I need teamviewer and ssh-agent to begin at startup. Do I just write them on rc.local as instructed?

---

### Post by darkod on 2013-01-07
I don't know.

But why did you install teamviewer, why not using the built-in Remote Desktop option? That starts by default.

The option to start at boot might be in the Teamviewer menu somewhere.

And is ssh-agent part of it, or not? The ssh server daemon is sshd I think and it starts by default, on the server. On the client you don't really need to start it at boot, you just connect a session when you want to. On the server you need it to run all the time. But i get a feeling ssh-agent is not part of the standard OpenSSH.

---

### Post by ivotkl on 2013-01-08
The thing is that I control my PC from my cellphone at times. Hence, If I do not have teamviewer running on both, it won't connect.

---

### Post by ivotkl on 2013-01-10
Shameless bump / update. Any ideas? I've tried adding them to rc.local file but it ain't working.

---

### Post by Lars Noodén on 2013-01-10
> **darkod said:**
> And is ssh-agent part of it, or not? The ssh server daemon is sshd I think and it starts by default, on the server. On the client you don't really need to start it at boot, you just connect a session when you want to. On the server you need it to run all the time. But i get a feeling ssh-agent is not part of the standard OpenSSH.

ssh-agent is only needed on the client side of things.  If you are running Ubuntu or a variant on your desktop, then the agent is already run when you log in.  

Another option for remote access would be SSHFS, which connect over SSH.

---

### Post by ivotkl on 2013-01-10
Thank you for the reply. However, I would need GUI access as well (it is not for File Transfer only) so that I can fix or solve problems.

---

### Post by ivotkl on 2013-01-12
Shameless bump. =(

---

### Post by darkod on 2013-01-12
Unfortunately, I don't have any more ideas, and it looks like nobody else does too (so far).

So, unless someone jumps in, I guess your choice is:
1. For full GUI access use the built-in Remote Desktop, which will work perfectly and by default it starts up with the system so it is always available.
2. Unless you find an option in Teamviewer saying something like "start at boot", I don't think you can use it as you want to, so it's going back to option 1 above.

That's it.

---

### Post by ivotkl on 2013-01-12
Okay, thank you very much.

How would I use the default remote desktop connection program?

---

### Post by darkod on 2013-01-12
This is just one short tutorial. I guess you can find many more on google and in the ubuntu documentation in help.ubuntu.com:
[http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/](http://www.unixmen.com/how-to-use-remote-desktop-in-ubuntu/)

When accessing over the internet I think the router has to forward the correct port to the private IP of the computer you are trying to access.

---

