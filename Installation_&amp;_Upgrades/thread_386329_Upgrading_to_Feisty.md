---
title: "Upgrading to Feisty"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by geovino on 2007-03-16
When Feisty is released next month, how will it be upgradible to Edgy users?

---

### Post by qamelian on 2007-03-16
> **geovino said:**
> When Feisty is released next month, how will it be upgradible to Edgy users?

When the final release is official, Update Manager will alert you about the new release when it checks for updates. There will be a button in the Update Manager to allow you to upgrade.

Also you can upgrade through Update Manager at any time by pressing Alt-F2 to get the run box and entering ```
gksu update-manager -cd
``` This will backup your current sources.list and create a new one with the Feisty repos in it. Not recommended to do this yet, as Feisty is still in testing,

---

### Post by tawniteamo on 2007-03-18
when I run:



   gksu update-manager -cd




I get:



                gksu: invalid option -- c
GKsu version 1.9.3

Usage: gksu [-u <user>] [options] <command>

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




any help would be appreciated, thanx.


realized what an idiot I was, its not gksu update-manager -cd it is gksu "update-manager -cd" I didn't know quotes were involved

---

### Post by silveris on 2007-03-18
try gksu update-manager -c -d

or

alt+F2 and then type gksu "update-manager -c -d"

---

### Post by geovino on 2007-03-24
> **qamelian said:**
> When the final release is official, Update Manager will alert you about the new release when it checks for updates. There will be a button in the Update Manager to allow you to upgrade.

Also you can upgrade through Update Manager at any time by pressing Alt-F2 to get the run box and entering ```
gksu update-manager -cd
``` This will backup your current sources.list and create a new one with the Feisty repos in it. Not recommended to do this yet, as Feisty is still in testing,

I ran the Feisty beta last night as live cd and I was impressed. Ubuntu has finally auto-mounted the drives so you can see them right away! That was my one gripe about Ubuntu for over a year and they finally made it happen!

I'm looking forward to it. Last year I had Dapper installed for a couple months and I did the upgrade to Edgy, but 75% through the upgrade my network connection hung up and after 30 minutes I rebooted the pc and lost it all. Any way to avoid the situation again?
Hopefully it won't happen.

---

