---
title: "Updated Ubuntu today new kernel, system now unstable"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by raynman on 2009-11-23
I uprgraded my Ubuntu today and the gnome desktop is unstable, the menu items are very unstable. If I go to click a menu it may or may not work. I now have a start up option of either 2.6.31-14 or 2.6.31-15 with or without recovery. I tried restarted and going to ..-14 but that did not help. I am really disappointed with this, I been upgrading regular because when ever I use one application with sound, the next application I try to use will not work with sound. I really don't wan't to rant here I really just won't to get my ubuntu 9.10 install working again. I am a recent Windows convert and I have been amazed at how much I prefer Linux and Ubuntu, but I now have completely unstable system, with now an extra startup option with no explaination why it is there,  Is completely perplexing to me, is the new kernel unstable? untested? I am more technical than the average windows convert and the distribution of and upgrade with multiple kernel options on startup, completey throws me. Are the Ubuntu developers serious about making an operating for a mainstream user? Is something wrong with my system that a new startup option magically appears?

I am going to stop asking questions and simply state a couple of observations.
I was new to Linux a few weeks ago and now have 3 installs.
The biggest issue by far for me has been sound. I have had issues with other O.S. with sound, so I understand some issues, however, I never had to fix the sound in the desktop, then troubleshoot other issues for 3D games, then try to fix why sound works for one application then breaks on other applications running in the desktop.

Secondly and finally, why the community support of Ubuntu is excellent, as their are a lot of helpful people, the lack moderation and expectation, that more and more less sophisticated users are using Ubuntu, and should be (in my opinion the audience of the Ubuntu forums) as more sophisticated users are not the target of the wide appeal of Ubuntu, is I feel worthy of observation. 

Make a great Linux distro for the average users, but please try to a least encourage support and dialogue that is both helpful and considerate of less sophisticated users.

I hope I didn't offended any one with this post, as I am sure I did, I just really think that what I said needs to be said, If only more eloquently.

---

### Post by Uss_Defiant on 2009-11-24
I've got the same issue... 2 new boot options in GRUB... when i go into -15 it shows the ubuntu logo, then goes to the command prompt... but the screen looks "shaky" and there's a lag time when typing... usually the keystrokes dont even register.

going into -14 is fine, and works like normal. Is there any way to fix -15? and to just boot into that? 

Thanks

---

### Post by xsilvergs on 2009-11-24
Hi,

Have a look at my thread here [http://ubuntuforums.org/showthread.php?t=1335464]("http://ubuntuforums.org/showthread.php?t=1335464") . To sum up, Iused the working Kernel Recovery and Repair Broken Packages. It found 7 packages broken / Partial Upgrade.

---

### Post by phillw on 2009-11-24
I've not booted in a while.. still running 14. I'll go get 15 and see how it behaves. As pointed out, if you find a new release causing problems, go back to the last stable one until you can find out what the problem is & how to fix it. It's why you should always keep at least one older kernel when you are housekeeping and removing old ones.

Phill.

---

### Post by phillw on 2009-11-24
Hmm, updated - no issues. The only thing I can think to try BEFORE you reboot is to go into update manager & get it to check for any updates.

Or issue

```
sudo apt-get update
```

Phill.

---

### Post by outdoorsman14 on 2009-11-24
I am in the same boat, but I don't see a kernel upgrade
I tried running Envy to update my display driver, rebooted and now it does the same flickering thing and won't let me login in the console display while doing it. It goes past the Ubuntu symbol but that is it. Is there a way to do updates without an internet connection, since I am at work and cannot connect it to our network?

---

### Post by phillw on 2009-11-24
> **outdoorsman14 said:**
> I am in the same boat, but I don't see a kernel upgrade
I tried running Envy to update my display driver, rebooted and now it does the same flickering thing and won't let me login in the console display while doing it. It goes past the Ubuntu symbol but that is it. Is there a way to do updates without an internet connection, since I am at work and cannot connect it to our network?

I'm currently over here -->  [http://ubuntuforums.org/showthread.php?p=8378128#post8378128](http://ubuntuforums.org/showthread.php?p=8378128#post8378128)

You're welcome to pop along and try out what we've done so far. As v15 worked fine for me, I'm struggling a bit on this one and am hoping we can put together a fully working solution.

I'm pretty sure you're going to need an i/net connection to do the updates, tho'

Phill.

---

### Post by dhavalbbhatt on 2009-11-24
I don't think xx-15 is a stable version of the kernal (I could yet be corrected on this one), the latest stable version is xx-14. If you want a stable system, there is no need to install xx-15. Even if you do, you should always keep the previous working version of kernal, just in case you need it. If you don't find xx-15 in synaptic (or its equivalent either using terminal or software center), and you absolutely need to, then go to your sources list and enable release/beta/untested version of software installbale on your computer (I am not sure of the exact wordings for that option and not in front of my Ubuntu machine right now).

---

### Post by ptn107 on 2009-11-24
These are the latest changes (2.6.31-15.50)[1] since the default kernel that was released with Ubuntu 9.10 (2.6.31-14.48)[2].  The kernel is NOT what's going wrong here.  Both of the -14 and -15 kernels are based on _stable_ 2.6.31.4.

```

linux (2.6.31-15.50) karmic-proposed; urgency=low

  [ Kees Cook ]

  * SAUCE: Fix nx_enable reporting
    - LP: #454285

linux (2.6.31-15.49) karmic-proposed; urgency=low

  [ Benjamin Herrenschmidt ]

  * [Upstream] (drop after 2.6.31) usb-storage: Workaround devices with
    bogus sense size
    - LP: #446146

  [ John Johansen ]

  * SAUCE: AppArmor: AppArmor wrongly reports allow perms as denied
    - LP: #453335
  * SAUCE: AppArmor: Policy load and replacement can fail to alloc mem
    - LP: #458299
  * SAUCE: AppArmor: AppArmor fails to audit change_hat correctly
    - LP: #462824
  * SAUCE: AppArmor: AppArmor disallows truncate of deleted files.
    - LP: #451375

  [ Kees Cook ]

  * SAUCE: [x86] fix report of cs-limit nx-emulation
    - LP: #454285

  [ Scott James Remnant ]

  * Revert "SAUCE: trace: add trace_event for the open() syscall"
  * SAUCE: trace: add trace events for open(), exec() and uselib()
    - LP: #462111

  [ Stefan Bader ]

  * SAUCE: Fix sub-flavour script to not stop on missing directories
    - LP: #453073

  [ Tim Gardner ]

  * [Upstream] (drop after 2.6.31) Input: synaptics - add another Protege
    M300 to rate blacklist
    - LP: #433801

  [ Upstream Kernel Changes ]

  * PM: Make warning in suspend_test_finish() less likely to happen
    - LP: #464552
 -- Stefan Bader <email address hidden>   Tue, 10 Nov 2009 14:31:52 +0100

```

[1] [https://launchpad.net/ubuntu/+source/linux/2.6.31-15.50](https://launchpad.net/ubuntu/+source/linux/2.6.31-15.50)
[2] [https://launchpad.net/ubuntu/+source/linux/2.6.31-14.48](https://launchpad.net/ubuntu/+source/linux/2.6.31-14.48)

---

### Post by phillw on 2009-11-24
> **ptn107 said:**
> These are the latest changes (2.6.31-15.50)[1] since the default kernel that was released with Ubuntu 9.10 (2.6.31-14.48)[2].  Nothing should be messing with the way the system boots.  Both of these kernels are based on _stable_ 2.6.31.4.

```

linux (2.6.31-15.50) karmic-proposed; urgency=low

  [ Kees Cook ]

  * SAUCE: Fix nx_enable reporting
    - LP: #454285

linux (2.6.31-15.49) karmic-proposed; urgency=low

  [ Benjamin Herrenschmidt ]

  * [Upstream] (drop after 2.6.31) usb-storage: Workaround devices with
    bogus sense size
    - LP: #446146

  [ John Johansen ]

  * SAUCE: AppArmor: AppArmor wrongly reports allow perms as denied
    - LP: #453335
  * SAUCE: AppArmor: Policy load and replacement can fail to alloc mem
    - LP: #458299
  * SAUCE: AppArmor: AppArmor fails to audit change_hat correctly
    - LP: #462824
  * SAUCE: AppArmor: AppArmor disallows truncate of deleted files.
    - LP: #451375

  [ Kees Cook ]

  * SAUCE: [x86] fix report of cs-limit nx-emulation
    - LP: #454285

  [ Scott James Remnant ]

  * Revert "SAUCE: trace: add trace_event for the open() syscall"
  * SAUCE: trace: add trace events for open(), exec() and uselib()
    - LP: #462111

  [ Stefan Bader ]

  * SAUCE: Fix sub-flavour script to not stop on missing directories
    - LP: #453073

  [ Tim Gardner ]

  * [Upstream] (drop after 2.6.31) Input: synaptics - add another Protege
    M300 to rate blacklist
    - LP: #433801

  [ Upstream Kernel Changes ]

  * PM: Make warning in suspend_test_finish() less likely to happen
    - LP: #464552
 -- Stefan Bader <email address hidden>   Tue, 10 Nov 2009 14:31:52 +0100

```[1] [https://launchpad.net/ubuntu/+source/linux/2.6.31-15.50](https://launchpad.net/ubuntu/+source/linux/2.6.31-15.50)
[2] [https://launchpad.net/ubuntu/+source/linux/2.6.31-14.48](https://launchpad.net/ubuntu/+source/linux/2.6.31-14.48)


Which kinda begs the question - Why are people having problems ? Whilst it *should not* cause any issues, it's quite evident from the posts that it *is.* So far, the solution *seems *to re-build broken packages. This points to the packages possibly being broken BEFORE the update, so I'd guess doing ```
sudo apt-get update
``` Before you boot into the new kernel *may* prevent it. As people aren't finding out until after they boot - it is quite scary to have no OS whatsoever. Hopefully the Ubuntu users are savvy enough to use their LiveCD to get on line and check for solutions 

Phill.

---

