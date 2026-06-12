---
title: "I've lost it. Can we bring it back?"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by nadabean on 2012-11-19
Thank you for acknowledging my request.

See, I'm a moderately experienced user. All along I've been blazing my own trail, learning linux a mono. I've painstakingly racked my back and brains sweating over an etherized distro, screaming in my head: <snip>

That's what this is about, only this time, the CPR isn't working--ubuntuforums, I don't know how to perform the operation that will bring this little Vaio back. I hope we could operate, surgically; but even a necromantic resurrection would suffice.

Okay, I'm gonna cut the metaphors: I need to either get my main account running or reformat and reinstall. Here's the issue:

My main account, the one with Admin privileges, has been disabled. Folly mine, admittedly, but the story is too long and complicated to recount here. And now I can only log in as a guest. Damn. What to do?

I tried logging in as root, but, fie, the root account isn't an option. My only access to root is in a read-only filesystem (what good is that?) and of course, sudo doesn't work. So, in a way, I fell on my own 'sword' as administrator of this machine.

Boo-hoo, cry me a river, I'll reformat and reinstall. 

WRONG!

The Vaio beautifully crafted with very few alternative boot options built in. There is NO USB BOOT OPTION!! That's okay, I'll just b-- NO CDROM DRIVE NEITHER, BOYO!!

<snip>

I *attempted* to network boot, that apparently *would* work. But as far as that goes, I'm completely forking lost to the science of server maintenance and all this non-sense about dphc's and tftp's and dhqrz's. I have no idea what any of it means or how to configure it correctly.

I've realized I have to pull the 'sword' out of my enormous ego, bleed, break down and admit I've finally been slain: I need help. 

What do I do? 

*grovel grovel*

---

### Post by darkod on 2012-11-19
When you enter the recovery mode and select Drop to root shell, you can remount as RW with:
```
mount -o remount,rw /
```

That should remount it as read-write, and since you are as root in the shell, you can try enabling the user, or resetting the password, depending what exactly you want to do and how you disabled it.

---

### Post by The Cog on 2012-11-19
If you hold the left shift key during boot, you should get a GRUB boot prompt. Edit the boot line and add the word **single** at the end, then boot. This should gain you a root prompt where you can reset the users password.

---

### Post by nadabean on 2012-11-20
Beautiful! Thank you both so much!

I'll be sticking around. 

Oh, and sorry about the "language" didn't realize I should hold my tongue.

Now I need to figure out what's going on with this ecryptfs command...

---

