---
title: "Have 11.10, want 13.10"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by nicholas.d on 2013-10-23
Two part question: 1) Is there a way to upgrade from 11.10 to 13.10 without having to use a CD with the ISO (my machine doesn't have USB boot)? 2) If not, will installing via CD cause a deletion of all my data files, applications, settings, etc?

---

### Post by Bucky Ball on 2013-10-23
If you are going to upgrade without a CD you are looking at doing it through the update manager which would mean 11.10>12.04>12.10>13.04>13.10.

I would expect problems doing this as it is a long road. Your other option is to wait until 14.04 comes out next year and go 11.10>12.04>14.04. As 12.04 and 14.04 are both LTS releases you can upgrade directly from one LTS to the next. LTS release have five years support. 13.10 has nine months (it will reach end-of-life when 14.04 LTS is due). Looking at how often you like to upgrade your OS, I would suggest you might be better off going with LTS releases. ;)

13.10 would be so different from 11.10 it might be a waste of time worrying about preserving settings and applications. They are well outdated on 11.10 (it hasn't been supported since April 2013).

---

### Post by nicholas.d on 2013-10-23
Bucky, when I try using update manager, this is all I get. Does this mean it can't be done without using CD? Thanks again...

---

### Post by Redalien0304 on 2013-10-23
go into software & Upadtes or sofware Sources bith sane thimg. cannot remeber what is called 11.10? go to updates Select Notify me of "For any version" or "for long-term support versions" both will work i Belive

---

### Post by Bucky Ball on 2013-10-24
Like Redalien0304 said. On the screenshot you have sent you can see the 'Settings' button at the bottom left corner. Hit that (in the real GUI, naturally), then go to the 'Updates' tab. Last line should read 'Notify me of a new Ubuntu version'. You might need to play around with that trying 'Long term release' or 'Any new release', as suggested.

The other issue is that 11.10 is not supported so this function may have stopped working. From memory, though, that was my guess on a thread about two weeks ago, but the user reported being able to upgrade to 12.04 LTS this way no problem. Give it a go. Good luck.

---

### Post by ptn107 on 2013-10-24
You're best bet and the safest, since you can't boot usb and you're release is no longer supported, would be to just give in and use a 13.10 iso image burned to a dvd.  You will have an installer option titled "Upgrade 11.10 to Ubuntu 13.10".  You're personal stuff will be kept and installed software kept where possible.

---

### Post by nicholas.d on 2013-10-25
Per Bucky's suggestion, I was able successfully upgrade 12.04 by changing going into Update Manager -> Settings and changing the "Notify me of a new Ubuntu version:" field value to "For any new version." After doing that, a box appeared within Update Manager saying "New Ubuntu release '12.04' is available," and it contained an enabled Upgrade button. Everything remained intact: my file folders, data files, software applications, etc.

---

### Post by Bucky Ball on 2013-10-25
Nice one! If you want to go any further you're going to need to do the same routine up to 13.04>13.10. You're at a stable LTS with a heap of support for now, though (til 2017), so why not wait until 14.04 LTS or beyond? You can always wait 16.04 LTS and that will be supported until April 2021. ;)

---

### Post by nicholas.d on 2013-10-31
So, against some of the advice above, I hard-headedly chose to upgrade rather than install from a new disk. I went thru all the upgrades from 11.10 to 13.10. Now my machine won't start all the way up. During the startup process, I get this message: 

"(!) The system is running in low-graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself." 

Then, I click OK. The next box that appears says:

"What would you like to do?
-Run in low-graphics mode for just one session
-Reconfigure graphics
-Troubleshoot the error
-Exit to console login"

If I select "-Reconfigure graphics" or "-Troubleshoot the error," then it gets caught in a loop. If I select "-Run in low-graphics mode for just one session," then it tries to continue starting up and then hangs indefinitely with a completely black screen. 

However, if I choose "Exit to console login," then I'm able to login and access the command prompt, but I don't know how to use Linux from there. Are there any steps I could take to restore graphics and login normally?

---

### Post by howefield on 2013-10-31
Are you using proprietary graphics drivers?

If so, uninstall them.

---

### Post by nicholas.d on 2013-10-31
Not that I know of. I mean, I didn't install any graphics drivers on top of whatever was included in 11.10.

---

### Post by Bucky Ball on 2013-10-31
Your issue now has nothing whatever to do with the title or original purpose of this thread.

I advise you mark this one as 'solved' (as you have indeed gotten from 11.10 to 13.10) and start a new thread in ***Multimedia & Video***. You will increase your chance of getting assistance. Thanks.

---

