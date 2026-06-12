---
title: "Awesome ubuntu 17.04!!! but why nothing works??"
date: 2017-04-27
forum: Installation &amp; Upgrades
---

### Post by kula1922 on 2017-04-27
I tell you the story... today morning when i wake up i saw the ubuntu upgrade! awesom!! I click 'upgrade' button... and then everything begin. After 1h of downloading and installing 'cool' news I got the new ubuntu. I typed in the console... oh wait... console not works... when i found a way to open a console and type there command 'pip3 install <something>' i got [COLOR=#242729][FONT=Consolas]ImportError: cannot import name '_remove_dead_weakref'.[/FONT][/COLOR] I will not bore you whole story because probably millions of people got  thousands crazy problems... after spend 12h for fixing the problems I gave up and say 'tomorrow i back to ubuntu 16.10' but now i am going to watch something... I put hdmi cable to port... and what? ubuntu 17.04 didnt see my tv... guys... can you stop break ubuntu? please... if you dont know how just DO NOT TOUCH IT!!!! DO NOT TOUCH!!!! it is enough good for use... why you again broke this good system???

ps. If you really wanna be helpfull tell me... how to downgrade it? why there is options?

---

### Post by TheFu on 2017-04-27
If you want a stable system, only use LTS releases. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)  Be certain to read the tables, notice the end of life dates, patterns, and scroll to the bottom. The others, like 16.10 and 17.04/.10 are "technology demonstration" releases, IMHO. The goal isn't stability, it is trying to show new technologies and see how they work towards becoming mature.

I don't know of any downgrade process except restoring from that full system backup made prior to deciding to do a dangerous upgrade process. BTW, all upgrade processes are dangerous.

Backups are a required things for all OSes and the #1 security tool that I know.

Lacking a backup, I think a fresh install is the only solution.  You might want to backup any system settings and data before beginning.

---

### Post by mörgæs on 2017-04-28
Short term support versions are not less stable than long and they are certainly not only technology demonstrations. For example, there was not much new functionality added in the move from 16.10 to 17.04, it was in some sense a bugfix release.

Kula, what you have seen is likely the consequence of a failed upgrade and not a problem with 17.04. I recommend a fresh install of 17.04 using wired internet access.

---

### Post by mastablasta on 2017-04-28
and furthermore , the graphics output is not managed by the OS but by GPU drivers. so make sure those are well installed.

---

### Post by ian-weisser on 2017-04-28
My new 17.04 upgrades work flawlessly on all my machines.

Whatever problem you have is not caused by Ubuntu.
Look for the real cause.

---

### Post by TheFu on 2017-04-28
> **ian-weisser said:**
> My new 17.04 upgrades work flawlessly on all my machines.

Whatever problem you have is not caused by Ubuntu.
Look for the real cause.

The point of a new release is to touch and upgrade as many packages to newer versions. Because you were previously running 16.10, there really isn't much choice about whether you will need 17.04 or not. You will, since in July support/patches for 16.10 will end.

I disagree with 2 of the other posters about the nature of non-LTS releases.  *New* isn't always better. Review the release notes: [https://wiki.ubuntu.com/ZestyZapus/ReleaseNotes](https://wiki.ubuntu.com/ZestyZapus/ReleaseNotes) to see if any of the known issues could be impacting your situation.

Non-LTS releases usually have new, untested-in-ubuntu, items included.  Unity was a technology demonstration in 11.04, a full year before 12.04.  Systemd was added before 16.04, in a non-LTS release.  Unity8 has been made available in 17.04, for example.  That certainly is a technology demonstration, which we know is a dead-end now. Unity8 is not the default, so you would have to go out of your way to use it.
I'm not trying to say that every new version of every project's package is untested or even unstable, but some clearly have known issues. Skimming the LVM warnings for any upgrade/new install will have me re-read that section and look for other considerations if I ever install 17.04.

Last week, I asked my LUG about their experiences with 17.04. Most of the comments had issues on at least 1 of their machines. Of course, people having issues are much more likely to respond. Only 5 people posted their experiences.  1 guy reported that out of 3 machines, only 1 was stable, then he did his weekly patching and all three of the systems were unstable.

Eventually things will be better, but it appears not yet.  The same things happen with most releases, we just have selective memory about those first few months. This is why waiting a few months after the release before installing it is a good idea for most people.  If you want stability, stick with LTS versions.

But if you've committed to running 17.04, then facts and data are needed to help.  Pick 1 thing at a time and post about only it.  I expect there is a different version of python installed, so any tools/programs/webapps you were using which depended on the OS version of python need to be revisited.  If you create your own apps using any of the scripting languages (go, perl, python, php, ruby, etc), it is a best practice NOT to trust the OS version of whatever language and use an environment management tool - rbenv, perlbrew, and I'm positive there's one for python. Doing this lets you control which version of the language is used for any application or for all your tools.  For little convenience scripts/utilities, I don't bother doing this, but for more complex webapps, I most definitely do setup entire development environments which are not dependent on the OS/distro versions of my language of choice.

I hope by now you have restored from a backup and everything is good with 16.10.

---

### Post by mörgæs on 2017-04-29
@Kula, don't think there is any complicated stuff hidden here. The release notes show that there are exceptionally few bugs in 17.04, and if you just do a standard install then chances are good that it will all work in first attempt.

Forget about what is said about LVM. Normal users having a computer with a single hard disk don't need it anyway.

---

