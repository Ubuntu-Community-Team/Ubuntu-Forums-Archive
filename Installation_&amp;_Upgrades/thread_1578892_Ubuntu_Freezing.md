---
title: "Ubuntu Freezing"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by comp_007 on 2010-09-21
Just installed ubuntu yesterday and it does not work !

Whenever I log-in after a few seconds ubuntu freezes !

I am using ubuntu 10.04.1 .

I am able to run it in failsafe mode and low graphics mode without any problem.

The internet hasn't been configured yet. . 

So right now I am posting through Win 7.

Please Help:confused:

P.S :- I am a beginner !

---

### Post by comp_007 on 2010-09-22
No replies ?

---

### Post by comp_007 on 2010-09-22
P.S -- I managed to connect internet in ubuntu. So ryt now I am using failsafe Mode which doesn't support any graphics !!

---

### Post by sikander3786 on 2010-09-22
Which graphics card are you using? Did you activate drivers for your card?

Also have you installed all the updates from the update manager?

---

### Post by comp_007 on 2010-09-22
I am using Intel 82945G/GZ Integrated Graphics Controller.

How to activate drivers ?

And yes, I have installed all the updates.

---

### Post by sikander3786 on 2010-09-22
You don't need to activate drivers for Intel Graphics. I think it is a problem related to compiz, try deactivating it for a moment and see if the freezes are gone. On the login screen press Ctrl + Alt + F1, login using your credentials in the console and type the following command.

```

 sudo chmod a-x /usr/bin/compiz

```

Then hit Ctrl + Alt + F7 and login to the Ubuntu desktop and see if it still freezes.

---

### Post by comp_007 on 2010-09-22
Ubuntu crashed while performing the above operation.

Now I am getting this message when i enter username password in Ctrl+Alt+ F1 screen

```
 unable to cd to '/home/username' 
```

Now I am unable to log into ubuntu any any means !!!

---

### Post by sikander3786 on 2010-09-22
Are you sure you typed the above command as stated there. I think you accidentally changed permissions on the home directory. What is the output of

```

ls -la /home

```

and

```

ls -la /

```

---

### Post by comp_007 on 2010-09-22
> **sikander3786 said:**
> Are you sure you typed the above command as stated there. I think you accidently changed permission of the home directory. What is the output of

```

ls -la /home

```

and

```

ls -la /

```

Where do I type these commands ?

---

### Post by sikander3786 on 2010-09-22
By hitting Ctrl + Alt + F1 at login screen. You'd have to post the output. Not easy typing all that stuff. Ok instead try to change permissions on your home directory regardless of what they actually are for now.

```

chmod 755 /home

```

Then restart by

```

shutdown -r now

```

And try to login when it reboots.

---

### Post by comp_007 on 2010-09-22
Sorry ,but I feel everything is going from over my head now !

Can you give a bit more detailed explaination please !!

Already I messed out my first step now don't want to mess up further.

---

### Post by comp_007 on 2010-09-22
> **sikander3786 said:**
> By hitting Ctrl + Alt + F1 at login screen. 

This prompts for username/password which ultimately gives the above mentioned error !
And the loop username/password loop is repeated again & again !!


> You'd have to post the output. Not easy typing all that stuff

If I reach there I would definitely do it !

 > Ok instead try to change permissions on your home directory regardless of what they actually are for now.

```

chmod 755 /home

```

Then restart by

```

shutdown -r now

```

And try to login when it reboots.

So that means I don't have to type the above commands which you mentioned in your previous post ?

And the same question goes.
Where to type this ?
Since Ctrl+Alt+F1 screen requires username / password.

---

### Post by sikander3786 on 2010-09-22
Sorry. Boot into recovery mode by pressing and holding down the shift key as soon as your computer gets past the Bios screen. Select recovery option probably the second one on the list. Select Drop to root shell and type chmod 755 /home there, then restart.

---

### Post by comp_007 on 2010-09-22
Got into the recovery mode.
Selected Drop Root shell

Typed chmod 755 /home 
and then restarted

After restarting ubuntu got stuck at the loading screen. I tried Ctrl+Alt +F1.
Typed username/password

But it still gave the same error *unable to cd to '/home/username'*

Pressed Ctrl+Alt+F7 to get back to the loading screen and then finally switched of the compter using power button from the CPU.

What should I do now ?

---

### Post by sikander3786 on 2010-09-23
Here is a similar thread and the OP unfortunately had to re-install.

[http://ubuntuforums.org/showthread.php?t=354643](http://ubuntuforums.org/showthread.php?t=354643)

---

### Post by comp_007 on 2010-09-23
Yes.

I reinstalled it yesterday only.Since it was a fresh installation I didn't mind it.

But the initital problem (Freezing one) still exists.

Is there another way to uninstall Compiz without risking much ?

---

### Post by comp_007 on 2010-09-23
I removed compiz packages using synaptic package manager.
That fixed the problem. I am able to run ubuntu in normal mode !

But,I want to install compiz also.
Is there a way to install compiz and run ubuntu normally ?

---

### Post by sikander3786 on 2010-09-23
Intel graphic chips have some history of problems with compiz. I used compiz on my dell gx280 with intel 915 chip 2 years back and it used to work well. Some intel chips have been on the compiz black list for some time. If it is not a critical/production machine, you can keep on testing otherwise I will advise to stay away if it is causing problems.

[http://ubuntuforums.org/showthread.php?t=1474759](http://ubuntuforums.org/showthread.php?t=1474759)

---

### Post by comp_007 on 2010-09-23
Well , thanks for solving all my quries.

And that means that I won't be able to run compiz desktop effects :(.
BTW , how do I know which intel graphic cards have been blacklisted by compiz ?

---

### Post by sikander3786 on 2010-09-23
The list for currently black listed cards is here.

[http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

Your card is not currently on the list but I'm pretty sure it has been there for some time.

The link is not opening here for now, it used to. I can only see a cached copy in Chrome.

---

### Post by comp_007 on 2010-09-23
Okey,Thanks for the link.

Its opening at my place perfectly !

Maybe after upgrading to ubuntu 10.10 this problem is solved !

---

