---
title: "How do I choose the snap version vs the repo version of a program?"
date: 2019-05-25
forum: Installation &amp; Upgrades
---

### Post by palteater on 2019-05-25
Hello

If I have installed say VLC both from the repository and the snap version, how do I choose which one to run?

I mean, if I type "vlc" + TAB in a terminal, I get to choose between "vlc" and "vlc-wrapper". I would expect to see something like "vlc" and "vlc-snap" or "vlc (snap)" or whatever.

If I go to the Show Applications and typ "vlc" I see two icons: "VLC Media pla..." and "VLC Media pla...", side by side. It would be great if thre was some kind of method to se what is what.

I search for snap info, and all I find are multiple statements that snap allows us to juggle versions of a program. It never tells how though, mostly just that there is a "revert" option that seems to downgrade the install, not add an older one next to the current. 

If I interpret things correct, I should theoretically be able to have ten different installs of VLC side by side - different versions, same versions, because they are all separately contained. So reasonably there must be some mechanism to choose which individ I am starting?

So: how do I discern between the snap version(s) and the repo version of a program? How do I choose between them? How do I know which one I am currently running?

This seems to be such a basic functionality that I bet I am missing something obvious.

Thanks in advance!

---

### Post by CatKiller on 2019-05-25
You might find this page helpful.

[https://itsfoss.com/use-snap-packages-ubuntu-16-04/](https://itsfoss.com/use-snap-packages-ubuntu-16-04/)

---

### Post by Holger_Gehrke on 2019-05-25
The binaries for the same program installed from a snap and from a .deb-package are normally named the same. Which one gets called depends on the order of directories listed in the variable PATH. Do 'echo $PATH' in a terminal. You should see '/snap/bin/' as the very last directory in the list. So if you just call 'vlc' in a terminal and have 'vlc' installed both from a snap and from a .deb, you'll get the version from the repositories. To call the snap-version you need to give an explicit path to the binary by using '/snap/bin/vlc' (which wouldn't actually be vlc but a link to /usr/bin/snap, which as the first thing it does checks the name it's been called with and then does a 'snap run name'). To switch between multiple revisions of a snap you use the 'revert' sub-command of 'snap' with the option '--revision', a revision number and the name of the snap. To see what snaps you have in what revisions, use 'snap list --all'.

The items in Show Applications and the various menus of the various Ubuntu flavours are generated from .desktop-files that can be found in various directories. The .desktop files for programs installed from snaps can be found in '/var/lib/snapd/desktop/applications'. Since the next update to a snap would wipe out any changes you make to these files it's better to override them by copying them to your personal directory for desktop files, which is located in $HOME/.local/share/applications and editing those copies. Since your personal directory is read last, any settings you put there override those made earlier. You can edit those files with any text editor, they are actually quite simple.

Holger

---

### Post by palteater on 2019-05-27
> **CatKiller said:**
> You might find this page helpful.

[https://itsfoss.com/use-snap-packages-ubuntu-16-04/](https://itsfoss.com/use-snap-packages-ubuntu-16-04/)

Yeah, thanks - no. That was among the first things I found and it does not mention what I am talking about.

---

### Post by palteater on 2019-05-27
> **Holger_Gehrke said:**
> The binaries for the same program installed from a snap and from a .deb-package are normally named the same. Which one gets called depends on the order of directories listed in the variable PATH. Do 'echo $PATH' in a terminal. You should see '/snap/bin/' as the very last directory in the list. So if you just call 'vlc' in a terminal and have 'vlc' installed both from a snap and from a .deb, you'll get the version from the repositories. To call the snap-version you need to give an explicit path to the binary by using '/snap/bin/vlc' (which wouldn't actually be vlc but a link to /usr/bin/snap, which as the first thing it does checks the name it's been called with and then does a 'snap run name'). To switch between multiple revisions of a snap you use the 'revert' sub-command of 'snap' with the option '--revision', a revision number and the name of the snap. To see what snaps you have in what revisions, use 'snap list --all'.

The items in Show Applications and the various menus of the various Ubuntu flavours are generated from .desktop-files that can be found in various directories. The .desktop files for programs installed from snaps can be found in '/var/lib/snapd/desktop/applications'. Since the next update to a snap would wipe out any changes you make to these files it's better to override them by copying them to your personal directory for desktop files, which is located in $HOME/.local/share/applications and editing those copies. Since your personal directory is read last, any settings you put there override those made earlier. You can edit those files with any text editor, they are actually quite simple.

Holger

That excellent answer exceeded my wildest expectations.

Extremely thanks, fine sir!

---

