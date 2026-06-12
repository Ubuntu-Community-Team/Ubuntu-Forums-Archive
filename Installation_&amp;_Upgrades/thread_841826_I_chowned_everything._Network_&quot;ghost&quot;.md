---
title: "I chowned everything. Network &quot;ghost&quot;?"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by yltv on 2008-06-26
Hello all-

In a recent attempt give myself rights on a folder, I thought it would be a good idea to "sudo chown hR admin /".

Unfortunately for me, I soon discovered that I could not even reboot the server because my sudo doesn't work. Well, I ended up at another thread which basically explained that I have killed my installation.

I have a working installation with configuration that I was planning on trying to copy to this server previously. Now I really need to do this.

Is there anyway to ftp an entire disk image, settings, users and all, from one server to another? 

Much like a network "ghost" ... 

I should also add that I don't have physical access to the server, it is 100 miles away. I need to restore it remotely.

Thanks in advance.

---

### Post by wdaniels on 2008-06-26
> **yltv said:**
> Is there anyway to ftp an entire disk image, settings, users and all, from one server to another? 

Much like a network "ghost" ...

There are ways to do what you want, only not if literally the only access you have to the server now is a non-root account on a broken system.

What other means of administering the server do you have? Is it a physical or virtual server? Is there someone the other end who could help you in any way?

---

### Post by yltv on 2008-06-26
> **wdaniels said:**
> Is it a physical or virtual server? Is there someone the other end who could help you in any way?

It's a physical server, installed in a cable headend. I could probably get someone to pop a CD in the server, but that's the extent of the help the cable company will give me.

If I send an install CD to the facility and have them pop it in, can I perform a recovery session through ssh?

---

### Post by DGortze380 on 2008-06-26
are you sure you toasted your system? I'm not sure how chown'ing a folder would mess up your sudoers file. try enabling the root account on the machine, and chown the folder back to your user. (unless ofcourse you're not the administrator and don't have rights to do that, in that case, call your sysmin). Is there another user account with sudo access that you have access to? 

To enable root:
```
 sudo passwd 
```

To switch to root:
```
 su 
```

If this works, BE CAREFUL chown what you need to and log out of root. I fyou haven;t toasted your system yet, you have a much greater chance of doing so as root!

If not, good luck, I'm sure these guys can try and help, they're awesome. Just take it as lesson learned, enable root as soon as you recover your system to avoid this situation.

---

### Post by yltv on 2008-06-26
> **DGortze380 said:**
> are you sure you toasted your system? 

If I wasn't sure before, I definitly am now. I just tried to SSH back in, and "the remote server unexpectedly ended the connection."

That was the first time I tried to connect since I logged out after the earlier chowning.

The server is online... I can ping it. 

I guess I'm taking a road trip to Natchez, where I'll re-install the OS...

I'll take it as a lesson learned...

Any good links for howto's if I want to create an image from another server to a DVD? This would make things much easier for the rebuild.

---

### Post by DGortze380 on 2008-06-26
> **yltv said:**
> If I wasn't sure before, I definitly am now. I just tried to SSH back in, and "the remote server unexpectedly ended the connection."

That was the first time I tried to connect since I logged out after the earlier chowning.

The server is online... I can ping it. 

I guess I'm taking a road trip to Natchez, where I'll re-install the OS...

I'll take it as a lesson learned...

Any good links for howto's if I want to create an image from another server to a DVD? This would make things much easier for the rebuild.

I'm sure some has a link, there is a command that will make an iso that you can then burn to a dvd.  If you have access other than through a network when you're there, you may be able to recover using a live cd to gain root access.

---

### Post by wdaniels on 2008-06-26
> **DGortze380 said:**
> are you sure you toasted your system? I'm not sure how chown'ing a folder would mess up your sudoers file. try enabling the root account on the machine, and chown the folder back to your user.

As I understand it he recursively chowned *everything* (/) to his own user, so that includes /etc/sudoers. And without sudo, you can't gain root to enable root login or anything like that. But it's not just /etc/sudoers that will be the problem now, changing ownership will have cleared the setuid bit on sudo itself and stuff like that.

> **yltv said:**
> If I send an install CD to the facility and have them pop it in, can I perform a recovery session through ssh?

I don't think a standard install CD will give you remote shell login by default, so unless you can also persuade them to open a terminal and apt-get install openssh-server for you...?

Otherwise, you could either construct your own installation CD with this installed by default, or perhaps find a live CD of some other distro which has a ssh server as standard. Once you've got a root shell remotely, anything is possible - that's the key.

But surely somebody at the cable company installed the OS on this machine initially? Couldn't you just backup your data and get them to re-install? Or is that going to cost money or something?

---

### Post by DGortze380 on 2008-06-27
> **wdaniels said:**
> As I understand it he recursively chowned *everything* (/) to his own user, so that includes /etc/sudoers. And without sudo, you can't gain root to enable root login or anything like that. But it's not just /etc/sudoers that will be the problem now, changing ownership will have cleared the setuid bit on sudo itself and stuff like that.



I don't think a standard install CD will give you remote shell login by default, so unless you can also persuade them to open a terminal and apt-get install openssh-server for you...?

Otherwise, you could either construct your own installation CD with this installed by default, or perhaps find a live CD of some other distro which has a ssh server as standard. Once you've got a root shell remotely, anything is possible - that's the key.

But surely somebody at the cable company installed the OS on this machine initially? Couldn't you just backup your data and get them to re-install? Or is that going to cost money or something?

Wrote off a live cd because Ubuntu Live doesn't have ssh... but ... I know Knoppix does. If you can get them to boot the machine with a knoppix live disk and click a couple buttons on the menu you can get ssh up and running. Ofcourse from there you still have to recover the system which my not be the easiest or quickest thing if you did recursively chown /.

---

### Post by yltv on 2008-06-27
> **wdaniels said:**
> 
But surely somebody at the cable company installed the OS on this machine initially? Couldn't you just backup your data and get them to re-install? Or is that going to cost money or something?

I configured it and then brought it to the site and installed it.

Here's what I plan to try:

1) Send the Knoppix disc to the site.
2) Have the cable guy pop the disc in.
3) Connect via SSH.
4) Somehow pull a disc image from the internet and have that image install itself on the machine.

But before I could do that, I'd have to create the disk image on the working machine, which I don't know how to do yet.

What's my best angle here?

I'd like to create an installer package that I could use "apt-get" and theoretically use on other servers with ease in the future.

This is going to be a pretty advanced project for me, but I think it is possible... Am I right?

---

### Post by DGortze380 on 2008-06-27
This will tell you how to make an iso of a hard drive:
[http://ubuntuforums.org/archive/index.php/t-6509.html](http://ubuntuforums.org/archive/index.php/t-6509.html)

As far as pulling the image off the internet. If I understand correctly, you have another remote machine that is working correctly that you want to image then blast that image onto the 'dead' machine??  SFTP will work but it will take a LONG time. Not sure of any other way though. For more about that:
```
 man sftp 
```

The only thing I haven't figured out (I was looking at doing something similar for a while) is how to then use that disk image and blast it onto the drive. I think you'd need some kind of software to do it correctly, Knoppix may even have something built in, I'd check that out first because I don't know if you can install programs on a knoppix live disc.

Searching around here might help you with getting ssh setup and the iso onto the drive:
[http://www.knoppix.net/forum/](http://www.knoppix.net/forum/)

Definitely let us know if/how this works!

---

### Post by wdaniels on 2008-06-27
I can think of a few ways to go about this. First, as you said yourself, would be a complete partition/filesystem image (à la ghost). If this is definitely the way you want to do it, I suggest you start by taking a look at [Partimage here]("http://www.partimage.org/Main_Page"). The only trouble with this kind of method is that it's mostly an "all or nothing" affair - once the image is written, it's either going to boot or it isn't and if you're unlucky then you're back to square one. You may want to pay some attention to the device names and numbers in grub boot files for example!

If this were me, I think I'd want to go for a more granular method that I'm sure is going to at least boot and run and let me log in remotely, then reconfigure the system by installing packages and changing config files. This can all be automated, but you have to put some effort in to finding the exact delta between a default installed system and the one you want to end up with. If you want to do it this way, I would suggest you first take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=819396") which explains various methods for retrieving a list of (and possibly also an archive of) installed packages then using that list/repository to re-install them all on another system. Config files are a bit harder and I won't go into that now since I expect you will probably use a partition image anyway ;)

The first method is potentially the quickest and easiest solution to your problem, but the second is ultimately a much more useful thing to do both for keeping track of and control over your server configuration and also learning a few things about Linux which (and I honestly don't mean to be offensive here) you probably ought to do considering the mistake you just made with chown :p :D

In any case, I should tell you that I've never done either of these things myself. I have a good idea of how to go about it all, enough to point you in some of the right directions, but I may not be the best person to guide you through everything. But hopefully if we discuss the matter in this thread it will bump enough times that somebody with some actual experience doing this will spot it! :D

---

### Post by yltv on 2008-06-27
> **wdaniels said:**
> I can think of a few ways to go about this. First, as you said yourself, would be a complete partition/filesystem image (à la ghost). If this is definitely the way you want to do it, I suggest you start by taking a look at [Partimage here]("http://www.partimage.org/Main_Page"). The only trouble with this kind of method is that it's mostly an "all or nothing" affair - once the image is written, it's either going to boot or it isn't and if you're unlucky then you're back to square one. You may want to pay some attention to the device names and numbers in grub boot files for example!

If this were me, I think I'd want to go for a more granular method that I'm sure is going to at least boot and run and let me log in remotely, then reconfigure the system by installing packages and changing config files. This can all be automated, but you have to put some effort in to finding the exact delta between a default installed system and the one you want to end up with. If you want to do it this way, I would suggest you first take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=819396") which explains various methods for retrieving a list of (and possibly also an archive of) installed packages then using that list/repository to re-install them all on another system. Config files are a bit harder and I won't go into that now since I expect you will probably use a partition image anyway ;)

The first method is potentially the quickest and easiest solution to your problem, but the second is ultimately a much more useful thing to do both for keeping track of and control over your server configuration and also learning a few things about Linux which (and I honestly don't mean to be offensive here) you probably ought to do considering the mistake you just made with chown :p :D

In any case, I should tell you that I've never done either of these things myself. I have a good idea of how to go about it all, enough to point you in some of the right directions, but I may not be the best person to guide you through everything. But hopefully if we discuss the matter in this thread it will bump enough times that somebody with some actual experience doing this will spot it! :D
I appreciate the pointers...

I will look at partimage tonight, probably won't get much sleep but hey that's the fun of it all right?

No offense taken, I really do need to learn more about this stuff. It's the times I've really messed up that I've learned the most...but that's life in general.

Anyway, bump, and I'll check in with more later.

---

