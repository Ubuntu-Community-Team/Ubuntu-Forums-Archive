---
title: "Self Control App Problems - Permanent block"
date: 2016-10-27
forum: Installation &amp; Upgrades
---

### Post by supadave on 2016-10-27
Hey Folks,

Beginner Ubuntu user here.

So, I installed Self Control, which is a website blocker/procrastination aid, on my laptop (macbook running 16.04), and added a couple of sites, gmail, facebook, to the block list, and now they're permanently blocked. Restarted, uninstalled app. Seems they are permanently blocked

It's exactly as described in this previous post, which is now closed even though it wasn't solved: [https://ubuntuforums.org/showthread.php?t=1725611](https://ubuntuforums.org/showthread.php?t=1725611)
I have tried what was suggested in that post-- deleting .config files, clearing cache with "BleachBit", and now I uninstalled the program, rebooted several times.

There is info from the developer here, including what seems to be some troubleshooting suggestions: [http://svn.jklmnop.net/projects/SelfControl.html](http://svn.jklmnop.net/projects/SelfControl.html) but I can't make sense of it, it's too complex for me.

I really don't want to reinstall ubuntu (again) just so that I can access gmail and facebook. Does anyone have any suggestions before I go ahead and do that. It seems that I should be able to figure this out in terminal somehow, but I have no idea where to start with that.

Thank you so much for your help,

Steve

---

### Post by kpatz on 2016-10-27
There's a "secret" page on the self control website that gives commands on how to uninstall it completely: [http://svn.jklmnop.net/projects/SelfControl/DONT_README](http://svn.jklmnop.net/projects/SelfControl/DONT_README)

In short, it uses iptables rules to do the blocking, and installs a script that runs iptables on each boot to reinstall the blocks.  The link above contains steps on how to remove that script and the iptables rules.

Also check your /etc/hosts files and remove any entries it may have added there.

---

### Post by supadave on 2016-10-27
Thanks for the quick reply. Hopefully you can help me decipher this a bit further. I had thought probably there was some valuable info on that page but I can't make heads or tails of it.

I took the commands listed at that site (originally I was put off by the "don't read me" as I thought I would screw things up further, again, I'm a novice). Not sure what to do with them, so copied and pasted each of the commands and ran them in terminal . Each one got me a response like below in italics.

I tried typing -d and d... can't really figure out what I'm supposed to do!

Anyway, here's what's showing up for me. Thanks again.
Steve

[I]gksudo iptables -F SelfControl
gksudo: invalid option -- 'F'
GKsu version 2.0.2

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
[/I]

---

### Post by kpatz on 2016-10-27
From a terminal, use "sudo" instead of "gksudo".

So instead of```
gksudo iptables -F SelfControl
```use```
sudo iptables -F SelfControl
```

If I have time, I'll install SelfControl in a VM and play around with it.

---

### Post by supadave on 2016-10-27
Ok, tried that. Terminal asks me for my password, which i enter, and then nothing happens. I could try using another one of the commands from that website, with "GK" removed?

What's a VM? Is that like a temp, trial OS where you can test things out before installing them?

---

### Post by kpatz on 2016-10-27
Some of the commands such as the iptables ones won't produce any output in the terminal (unless you get an error) but they're doing things.  Do all the commands using sudo instead of gksudo and see if you get your websites back.

Just running the iptables commands should get your access back but if they are blocked the next time you reboot you'll need to run the other commands to remove the startup script.

VM is a virtual machine (I use Virtualbox).  I use them for experimental purposes when I don't want to molest my live OS.  I can take a snapshot, install something, play with it, then revert the snapshot to bring things back to their "unmolested" state.  Handy for testing applications that may not uninstall completely, or to play with different operating system versions without having to tie up a physical computer for each OS.

Make sure to edit your /etc/hosts file too.```
gksudo gedit /etc/hosts &
```You use gksudo for this since it's a GUI application.  Delete any lines referencing your blocked websites and save the file.

---

### Post by kpatz on 2016-10-27
I just messed with it in a VM, the uninstall steps in the link I posted earlier work fine, as long as you use sudo instead of gksudo, and edit the /etc/hosts file as well.

The reason some people find sites blocked permanently instead of just for the specified time is because the "at" package isn't installed.  at is a tool that allows jobs to be submitted that run at a certain time in the future; it's what SelfControl uses to unblock sites after the specified time.

If you want to use SelfControl and have the sites unblock after the specified time, use the command:```
sudo apt-get install at
```

If you don't want SelfControl, the uninstaller seems to work and it cleans things up:```
sudo dpkg --purge selfcontrol
```

And last but not least, if you want a way to block distracting websites that works a bit better, consider adding the LeechBlock add-on into your browser (Firefox has it available, and I think Chrome does too).

---

### Post by supadave on 2016-10-28
All right!
gksudo gedit /etc/hosts
did the trick!

I have really no idea what exactly I did though. Or what the diff between sudo and gksudo is. Or really what sudo is!

In future, does it make sense at all to get a VM to test out changes I want to make to the system? It sure seems like a bit of a mine field at the moment for me.

SThanks for your help! I really really really appreciate it.
SSteve

---

