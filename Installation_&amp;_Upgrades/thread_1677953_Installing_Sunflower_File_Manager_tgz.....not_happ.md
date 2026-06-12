---
title: "Installing Sunflower File Manager tgz.....not happening"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by Splat_NJ on 2011-01-29
I d/l the Sunflower File Manager tgz file to install into Ubuntu. I already have the Build-Essential package installed. When I go to the directory I extracted the Sunflower's tgz files to and type in a shell "./configure" I get an error: "bash: ./configure: No such file or directory"  Well, yes... looking into the Sunflower directory there is no such file or subfolder there. Now I admit I'm not an Ubuntu expert but IIRC I've done a few tgz installs like this and they went fine. What am I doing wrong here? Thanks.

---

### Post by oldos2er on 2011-01-29
It's a Python app. In a terminal, "cd" to the Sunflower folder, and run **python ./Sunflower.py**

---

### Post by Splat_NJ on 2011-01-29
Thank you, Ann.  I'll give this a shot. BTW, I'm also an old DOS person, myself. :)

---

### Post by Splat_NJ on 2011-01-29
Well Ann, it worked, but I get this error upon executing:

WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'

I think I'll stick with Nautilus for now. I really wanted something with dual panes, but how hard is it to hit F3 for the extra pane anyway..? :) Thanks again.

---

### Post by oldos2er on 2011-01-30
There is Gnome Commander, a two-pane file manager that's available in the repositories. ```
sudo apt-get install gnome-commander
```

---

### Post by MeanEYE on 2011-02-09
> **Splat_NJ said:**
> Well Ann, it worked, but I get this error upon executing:

WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'

I think I'll stick with Nautilus for now. I really wanted something with dual panes, but how hard is it to hit F3 for the extra pane anyway..? :) Thanks again.

Hi there Splat_NJ. Warnings you get when running Sunflower from terminal are actually not the problems within program itself. I am not sure why this is happening and it bothers me as much as it does you. If you start any other program you'll see a number of others warnings regarding menus and similar stuff. In my opinion these warnings are generated in python bindings.

You shouldn't worry about this though as program works as expected. Sorry you didn't find it useful and program is still in early alpha stage. I am however pushing a new version each Sunday so if you have any features you'd like to have just let me know and I'll make something happen.

Thanks again for trying! :)

---

### Post by Splat_NJ on 2011-02-09
Thanks MeanEye. I think I'll try it out again then. Thanks for creating the program.

---

### Post by MeanEYE on 2011-02-13
> **Splat_NJ said:**
> Thanks MeanEye. I think I'll try it out again then. Thanks for creating the program.

You are most welcome. Am just glad there are people interested in it. If you need help, please let me know. :)

---

### Post by chevy57 on 2011-06-04
I have the problem that the program does not start after I upgraded from Sunflower-0.1a-27 to Sunflower-0.1a-28.:(
When I downgrade, it works again.
 I have this error in terminal
---------------------------------------------------------------------------------------
Trying with python2.7...
Traceback (most recent call last):
  File "./application/main.py", line 28, in <module>
    app = MainWindow()
  File "/home/zillen/Sunflower-0.1a-28/application/gui/main_window.py", line 101, in __init__
    self._version_specific_actions()
  File "/home/zillen/Sunflower-0.1a-28/application/gui/main_window.py", line 1237, in _version_specific_actions
    change_log = ChangeLogDialog(self, vbox, not mod_count == 0)
  File "/home/zillen/Sunflower-0.1a-28/application/gui/changelog_dialog.py", line 121, in __init__
    frame.add(hbox1)
UnboundLocalError: local variable 'hbox1' referenced before assignment
----------------------------------------------------------------------------------------
someone who can help me get a very good program running again

I solved the problem by deleting the folder ~. / config / sunflower, can also be put on ~. / sunflower. Then started the program as it should.

---

### Post by MeanEYE on 2012-03-05
> **chevy57 said:**
> I have the problem that the program does not start after I upgraded from Sunflower-0.1a-27 to Sunflower-0.1a-28.:(
When I downgrade, it works again.
 I have this error in terminal
---------------------------------------------------------------------------------------
Trying with python2.7...
Traceback (most recent call last):
  File "./application/main.py", line 28, in <module>
    app = MainWindow()
  File "/home/zillen/Sunflower-0.1a-28/application/gui/main_window.py", line 101, in __init__
    self._version_specific_actions()
  File "/home/zillen/Sunflower-0.1a-28/application/gui/main_window.py", line 1237, in _version_specific_actions
    change_log = ChangeLogDialog(self, vbox, not mod_count == 0)
  File "/home/zillen/Sunflower-0.1a-28/application/gui/changelog_dialog.py", line 121, in __init__
    frame.add(hbox1)
UnboundLocalError: local variable 'hbox1' referenced before assignment
----------------------------------------------------------------------------------------
someone who can help me get a very good program running again

I solved the problem by deleting the folder ~. / config / sunflower, can also be put on ~. / sunflower. Then started the program as it should.
Sorry for not replying earlier. This thread somehow got away from me. :) 
You can always find some more help with Sunflower on our projects page over at code.google.com/p/sunflower-fm or #sunflower at irc.ubuntu.com

Cheers!

---

### Post by Splat_NJ on 2012-03-05
No problem, Meaneye.  Just wanted to thank you for replying, however I've went back to the dark side.  I got tired of trying everything I read/heard to get the video and audio playback smooth on my Ubuntu install but could never get it. Always stuttering with video playback and can't open more than 1-2 windows without stuttering.... I had it.  Maybe in another year or less I'll try Ubuntu or some other build again but it's a shame. I liked it but ... maybe another time. Thanks again anyway.

---

