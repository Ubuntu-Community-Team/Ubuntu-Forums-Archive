---
title: "Lexmark Z600 driver install problems"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by tapman1 on 2010-03-22
I am trying to get my Lexmark X1185 to work and was trying to use the directions in a post from black hole sun. I replied to the post asking directions, but have not had a response. I was able to follow the directions of his post to this point. The command line that has stopped me is as follows:

sudo tar xvzf  z600llpddk-2.0.tgz -C

I get the following error code:

tar: option requires an argument -- C
Try `tar --help' or `tar --usage' for more information.

I don't quite understand how to correct it and finish the install. It seems that v9.04 doesn't work the same way as his post directs, since the thread was posted in 2005.

Could I get some direction on how to finish the install and get my printer working.

Thanks,

---

### Post by anglican on 2010-03-23
> **tapman1 said:**
> I am trying to get my Lexmark X1185 to work and was trying to use the directions in a post from black hole sun. I replied to the post asking directions, but have not had a response. I was able to follow the directions of his post to this point. The command line that has stopped me is as follows:

sudo tar xvzf  z600llpddk-2.0.tgz -C

I get the following error code:

tar: option requires an argument -- C
Try `tar --help' or `tar --usage' for more information.

I don't quite understand how to correct it and finish the install. It seems that v9.04 doesn't work the same way as his post directs, since the thread was posted in 2005.

Could I get some direction on how to finish the install and get my printer working.

Thanks,

Just use the command without the "-C" - which as tar is trying to tell you is not a valid option.

H

---

### Post by tapman1 on 2010-03-23
Thanks for replying. It did not work leaving the -C off the command string.

Here is the error I get now.

tar: z600llpddk-2.0.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I would like to add that the files exist on the desktop. 

Should I move them to another folder??

---

### Post by tapman1 on 2010-03-23
I got it to go past the command by changing to the Desktop folder. It unpacked and seemed to place the files correctly.

I then was not able to run the subseqent command "sudo tar xvzf zcups600-1.0.tgz -C"

It seems that the file doesn't exist.

Any suggestions?

---

### Post by anglican on 2010-03-26
> **tapman1 said:**
> I got it to go past the command by changing to the Desktop folder. It unpacked and seemed to place the files correctly.

I then was not able to run the subseqent command "sudo tar xvzf zcups600-1.0.tgz -C"

It seems that the file doesn't exist.

Any suggestions?

OK, I finally read what you posted properly! The tar command you typed is incomplete, the -C option requires something to follow it, in this case it should be / (go and look closely at your source for this command). I suggest you start from the very beginning and use:

sudo tar xvzf zcups600-1.0.tgz -C /
--------------------------------------------^ note the "/" character!
etc...

The commands you have been using are incomplete.

H

---

