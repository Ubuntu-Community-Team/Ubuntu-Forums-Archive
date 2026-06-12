---
title: "Share KDE-Data among Distris"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by walt+walt on 2007-09-14
I have Feisty, Gutsy and Debian installed. All Distros use KDE resp. Kontocat.

Smart, as I am, I thought it great to create a separate partition containing everything in regard of Kontact. I did this with sym-link (soft ones). Now, the problem is, that sometimes a symlink gets forgotten by a distro (when I log-off and log-on) and e.g. creates in .kde a new kmail folder- I then go and delete that one and make the symlink again. 
Now, I am lokking for a script who does all this work for me. The script should do this:

1) check if the symlinks are still there (kontact -> kmail, korg, .......)
2) if yes, jupedidoo
3) if not, delete newly (auto) created Folders and set the symlinks again.

Is this something hard to to? Could somebody please give me a starter ? Just some lines so I can create the rest myself.

Many, many thanks in advance,  walt

---

### Post by mkoyle on 2008-01-09
I am not totally certain I understand how your symbolic links get changed into directories... anyway, you might just write a script that deletes the links / directories and then sets them again.  You could then add the script to your boot up or perhaps to your gnome session's log on and it should generally fix itself.

maybe something like:

```
rm link
rm link
rm -r dir
rm -r dir

ln -s target link
ln -s target2 link
```

Does that make sense to you?

As far as making it run automatically, [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F)  probably is the answer:

> If you need to execute something after you log into your Gnome session, then all you need to do is choose System>Preferences>Sessions from the menu, choose the "Startup Programs" tab, and add the path to whatever script/program you want to run at startup of session.

That link also tells how to make something run right at bootup.

By the way, I noticed that you were having trouble with java on a 64-bit system.  Have you sorted that out or did you just decide to run 32-bit?  I was just checking up on [https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/152362](https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/152362) and seeing if anyone had found any better solutions.  Currently, building java fixes it for me.

--Matthew

---

### Post by mkoyle on 2008-01-09
If you are still looking to make a script that tests whether something is a symbolic link, [http://tldp.org/LDP/abs/html/testconstructs.html](http://tldp.org/LDP/abs/html/testconstructs.html) talks about tests and [http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html) has a list of types of tests.

It seems that 
```
if [ -h /dir/dir/link ]
```
is pretty close to what you originally asked for.  I created a link and ran a pair of commands to see if it worked:

```
matthew@Judith:/home/shared$ sudo ln -s Taxes tax 
matthew@Judith:/home/shared$ ls -l tax
lrwxrwxrwx 1 root root 5 2008-01-09 00:10 tax -> Taxes
matthew@Judith:/home/shared$ if [ -h tax ]; then echo abc; fi
abc
matthew@Judith:/home/shared$ if [ -h taxi ];  then echo abc; fi
```
That last one was just a check to make certain it would not perform the command if there were no symbolic link at the location specified.

So maybe what you were looking for is:
```
if [ -h link1 ] 
   then
      echo link1 is fine
   else
      rm -r link1
      ln -s source_of_link1 link1
fi

if [ -h link2 ] 
   then
      echo link2 is fine
   else
      rm -r link2
      ln -s source_of_link2 link2
fi
```

If you don't need or want the output, maybe the following is better:

```
if [ ! -h link1 ]
   then 
      rm -r link1
      ln -s source_of_link1 link1
fi

if [ ! -h link2 ] 
   then 
      rm -r link2
      ln -s source_of_link1 link1
fi
```

I admit I am something of a novice at bash scripting, but from here you should be able to figure out what you need.

One last note, another poster was trying to compare the contents of files; the post looks semi unresolved, but might be helpful: [http://ubuntuforums.org/showthread.php?t=632688](http://ubuntuforums.org/showthread.php?t=632688) .

--Matthew

---

