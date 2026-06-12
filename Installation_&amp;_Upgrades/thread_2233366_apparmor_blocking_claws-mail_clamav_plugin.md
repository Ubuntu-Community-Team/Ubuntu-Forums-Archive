---
title: "apparmor blocking claws-mail clamav plugin"
date: 2014-07-08
forum: Installation &amp; Upgrades
---

### Post by a-you on 2014-07-08
I just installed ubuntu studio trusty 64 bit (though I get the impression from searching that this is a problem that's not specific to ubuntu studio at all).

I installed apparmor-notify and thanks to that I'm notified that apparmor seems to be not letting the clamav plugin for claws-mail scan email. Yes, I have read many times that scanning email is not even necessary in gnu/linux, but anyway...

In spite of all the comments everywhere that apparmor is easy to configure I must say that to me it doesn't seem so obvious (I'm not a programmer, and not too geek) how to edit the apparmor profile for clamd such that apparmor lets it do its work. For the moment I have set apparmor to just complain about clamd and also uninstalled the claws clamav plugin; that's a fine solution I guess, but it would be nice to solve it for real if that's easy enough.

I guess what I'm asking is whether anybody can point me to an existing apparmor profile for clamd that fixes this, or knows of a tool or tutorial that really is for total apparmor n00bs---real simple step by step stuff.

I don't find aa-easyprof to be all that easy frankly. Unless I'm missing something.

Thanks in advance.

---

### Post by a-you on 2014-07-08
I may have fixed it but please anybody that knows apparmor, if you would be so kind as to comment I'd appreciate it. In case it's totally the wrong thing to do.

What I did was to put apparmor into "complain" mode for test purposes, and re-enable the claws plugin. Then after sending myself test emails I looked at kern.log and it looked like the issue was that clamd wanted to open a file in a particular directory. I should explain first though that I had some time ago moved all email stuff to a folder inside of ~/Private (that is, I don't use an encrypted  home folder but I do have a "Private" encrypted folder created with ecryptfs). In each case, from the log it looked like clamd wanted access to a file that had a long obviously encryoted filename. It seemed to want write access.

Anyway I added the following lines to the usr.sbin.clamd apparmor profile and it seems to be working:

```
   /home/my_user_name/.Private/** rw,
  /home/my_user_name/.Private/* rw,
```

[edit:] come to think of it maybe that "file" it wanted to access was a directory??? And I can think of other reasons why write access would make sense. Still though, comments from people more expert in these matters would be very nice (thanks).

---

### Post by a-you on 2014-07-10
Huh. That seems to have solved it. Whew.

I've been checking kern.log since modifying that profile and there are no problematic looking entries. Uh, I guess a real test would be to send myself an infected email, but I don't want to get into that...

Hopefully this info helps somebody somehow.

---

