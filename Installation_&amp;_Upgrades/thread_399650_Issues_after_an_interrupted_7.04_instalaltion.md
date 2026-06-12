---
title: "Issues after an interrupted 7.04 instalaltion"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Yaraher on 2007-04-02
I was trying yesterday to update my Edgy installation to the latest beta by using the "update-manager -c -d" command on the terminal.

It run smoothly, downloaded all the content and started the installation. Then... my brother needed to print some file he was working on, so I told him to connect my printer on my other PC, while that one kept installing. However, accidentally he disconnected the power supply of that PC instead of the printer one.

So, now the installation never finished, and I no longer can start Ubuntu (which sounds logical considering what happened), the computer showing a "Unable to boot root filesystem" message. 

I loaded my 6.06 cd, and try installing it, but found that I had to format the "/" partition in order of it to install. And it happens that this machine only has a swap a / partition, no "/home" partition apart. There are a lot of files over there, so erasing them isn't an option :) 

Is there any way to continue the installation or reverse the changes with the LiveCD? Or any way to install 6.06 without formatting the partitions and thus, I'd guess, preserving the Files?

---

### Post by Majorix on 2007-04-02
I am afraid there is no way to continue the installation from where it left off. Imagine this: You are developing a brand new idea, thinking. Then someone comes and hits your head with a club. You manage not to die but your brain is so heavily damaged that you can't think anymore. Do you think now it is possible to develop that idea further?

You don't have to delete your files. Just back them up on DVDs or CDs for that matter and do a fresh reinstall from a daily build 7.04 CD and everything should run smoothly.

Sorry again.

---

### Post by zvacet on 2007-04-02
if you can go to the terminal from live CD try this.
```
cd /var/cache/apt/archives
```
and when you are in
```
dpkg -i *deb
```

If it works should install all files you downloaded

---

### Post by Majorix on 2007-04-02
That might cause problems with the system performance later on. Take the example I have given.

I still suggest a clean install.

---

### Post by Yaraher on 2007-04-02
That seemed logica afterall (I'm a software developer, so I know how installations works, but since Linux has surprise me so much since I started using it, I said to myself, who knows, maybe it's possible here! :P)

The main issue I have now then is that the PC doesn't have a CD Recorder. I'll try to copy the files over the network (a bit edgy so far, but I'll take a shot at it again). However, since this is my Dad's computer, I'm not sure if he has the installers of the software he installed there (software that doesn't resides on the Synaptic repositories, but that he downloaded himself.

Is it possible to copy a folder, install the new 7.04 and copy that folder back and have all it's applications there? I work at a Mac, and it works like that, so I'd assume it is possible in Linux (I am, on overall, a really new user to Linux. Have used for some years now, but mostly as a desktop user.). 

zvacet: That sounds good too, but does it knows which one to start installing first? I'd figure there is a script with an order somewhere that dictates that.

Thanks for your help so far!

---

### Post by Majorix on 2007-04-02
> Is it possible to copy a folder, install the new 7.04 and copy that folder back and have all it's applications there? I work at a Mac, and it works like that, so I'd assume it is possible in Linux (I am, on overall, a really new user to Linux. Have used for some years now, but mostly as a desktop user.).

The thing is that 7.04 is using a new kernel (GNU/Hurd) so I am not sure if it is possible to do that. It *could* work from 6.06 to 6.10 but no not from 6.10 to 7.04.

---

### Post by Yaraher on 2007-04-02
Since my system used to be 6.10 when the programs were installed, I'd guess it could be fine?
Which folder should I copy to preserve the installed applications?

---

