---
title: "Held back NVidia packages on 22.04"
date: 2022-05-17
forum: Installation &amp; Upgrades
---

### Post by mauro87 on 2022-05-17
[COLOR=#1A1A1B][FONT=&amp]So I clean installed 22.04 on the day of release and have been upgrading with sudo apt upgrade without issue. Today, I got the following message about kept back packages when trying to run the command:
[https://imgur.com/a/wCmgrhc](https://imgur.com/a/wCmgrhc)
I did some research and apparently it means that some packages have dependencies that have changed. There was a video about this on techrepublic that mentioned I can fix this safely by installing aptitude and running sudo aptitude safe-upgrade. I'm holding off for now because I've been burned before with Nvidia updates breaking my system and I need this for work. Can anyone confirm that sudo aptitude safe-upgrade is, indeed, safe? If not, what can I do to install these new dependencies?
[/FONT][/COLOR]

[FONT=inherit][COLOR=#878A8C][FONT=IBMPlexSans][FONT=inherit][FONT=inherit][FONT=inherit]0[/FONT]0[/FONT]
[/FONT][FONT=inherit]Comments[/FONT][/FONT][/COLOR]
[COLOR=#878A8C][FONT=IBMPlexSans][LEFT][FONT=inherit]Share[/FONT][/LEFT]
[/FONT][/COLOR]
[COLOR=#878A8C][FONT=IBMPlexSans][FONT=inherit]Save[/FONT][/FONT][/COLOR]

[COLOR=#878A8C][FONT=IBMPlexSans][COLOR=var(--newCommunityTheme-actionIcon)][/FONT][/COLOR][FONT=IBMPlexSans]
[/FONT][/COLOR]
[/FONT]

---

### Post by Bashing-om on 2022-05-17
mauro87; Hello

Let us suppose that you are on X11 vice Wayland with Nvidia graphics. Nvidia has directed us to remove their proprietary driver for use in Wayland.

Now directly to your issue at hand.
As we have "22 not upgraded"; let us direct attention there for the time being.
Run in terminal:
```

sudo apt update
sudo apt full-upgrade

```
and post these results back here, directly to this thread
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we will see what there is yet to do.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by mauro87 on 2022-05-17
> **Bashing-om said:**
> mauro87; Hello

Let us suppose that you are on X11 vice Wayland with Nvidia graphics. Nvidia has directed us to remove their proprietary driver for use in Wayland.

Now directly to your issue at hand.
As we have "22 not upgraded"; let us direct attention there for the time being.
Run in terminal:
```

sudo apt update
sudo apt full-upgrade

```
and post these results back here, directly to this thread
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we will see what there is yet to do.[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


Hello, Bashing-om. It worked! I ran the command, crossed my fingers and rebooted and everything is fine now. I was really nervous since I've been burned before. Should I be running this command in future if there are held back packages? I did some research and it looks like this command "Removes old packages if needed to perform the upgrade of packages to their latest versions".

---

### Post by Bashing-om on 2022-05-17
mauro87; Hey !

Pleased things worked out -
"held back packages"  is a fairly rare condition. I many such cases just waiting on the mirror/system cache/mother to sync up will resolve.

In any event running " full-upgrade" will not hurt a thing - though generally " sudo apt upgrade" is good enough.
But. remember one must always "sudo apt update" to sync up the respective data bases - if doing these from terminal. 

Here in this instance I would suppose that the 22 packages not updated to be a prime factor.

If this matter is now concluded to your satisfaction >>
 Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by mauro87 on 2022-05-17
> **Bashing-om said:**
> mauro87; Hey !

Pleased things worked out -
"held back packages"  is a fairly rare condition. I many such cases just waiting on the mirror/system cache/mother to sync up will resolve.

In any event running " full-upgrade" will not hurt a thing - though generally " sudo apt upgrade" is good enough.
But. remember one must always "sudo apt update" to sync up the respective data bases - if doing these from terminal. 

Here in this instance I would suppose that the 22 packages not updated to be a prime factor.

If this matter is now concluded to your satisfaction >>
 Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)[INDENT][INDENT]up up and away
[/INDENT]
[/INDENT]


Done, marked as solved! I usually run ```
sudo apt update && sudo apt upgrade
``` so I'm not sure why they were held back. In any event, everything is working as intended so I'm happy. Thanks again!

---

### Post by grahammechanical on 2022-05-17
The command "apt full-upgrade" seems to be less risky than the "apt-get dist-upgrade" command.

Compare what you have read about full-upgrade

> "Removes old packages if needed to perform the upgrade of packages to their latest versions".

with what the man page says about dist-upgrade

> dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages.

The full-upgrade command replaces older packages with newer versions. The dist-upgrade command will remove packages where there is a conflict in order to resolve the conflict. It can result in a broken system.

Regards

---

