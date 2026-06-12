---
title: "Get Duplicate Sources Warnings, But sudo apt-get update does not fix problem"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2015-10-31
I do "**sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get autoremove**" in a terminal window daily to keep my Ubuntu 14.04 install up to date.  Actually you can do it with any Debian distro, and I've been doing it since Ubuntu 8.04 and will keep doing it.

But while the update process works fine (except that apt does not know about chromium and Ubuntu Software Center does, while USC does not know about cream and apt does),
I'm getting warnings from apt now on the screen that are not being put there by stdout or stderr.  I know because I cannot redirect them to a file.

Anyway, here is a copy&paste from the terminal screen:
```
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com/ubuntu/ trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
W: **_You may want to run apt-get update to correct these problems_**

```
A quick look shows that i386 packages are getting mixed in there.  That's 32-bit, and I am running 64-bit now.  I did install a magnifier program that would not run because it required a library that was not available via the normal channels, and the only found resources were 32-bit.  I don't want to mix 32-bit code with 64-bit if I can help it, and besides, I found that the dconf-editor, gnome-tweak-tool, and unity-tweak-tool will together give you access to most cases of picking a font and size to improve readability.  Other than that, you have to see if the applications give you settings you can change, a zoom feature, or instructions online on how to change their settings.  I no longer need a screen magnifier at all.

What bugs me though is that the bold, underscored "fix" is no fix at all.  Every time around. I get the same warnings.  So how do I fix this?

I've run "**sudo apt-get update**" separately, and it is not a help either.  I've also run sudo "**apt-get upgrade**" and that was no help.

---

### Post by ajgreeny on 2015-10-31
Can you please show us the total output in terminal of ```
cat /etc/apt/sources.list
``` and we can then tell you which lines to remove or comment out (add a # at start of line).

---

### Post by oldefoxx on 2015-11-05
I did better than that.  I went and looked at where it was reported that the duplicate was found.  There is no way a simple user like myself can cope with the guts of a file like that.  I learned by a short study of it that there are plenty of i386 modules in the 64-bit version, which is something I qas not aware of.  So I could ignore the fact that I was getting warnings for both amd64 and i386, because they were not handled on that basis in the  /etc/apt/sources.list file.  It was possible that one entry could cause both warnings, and with a further divison over i386 and amd64, could have caused the original four warnings,

I also realised the quickest and easiest way to find sources.list, if you forget where it is, is to open a Terminal and type in "locate sources.list"  The response is immediate.  The right answer is usually the topmost one.  You can then type in "sudo gedit " and copy & paste the whole path using the mouse to highlight the portion to be copied, then Ctrl+Sjft+C to copy that to the clipboard, then immediately use Ctrl+Shft+V to paste it into the new command.  Hit Enter, and you are in the file itself.

I learned that taking the original on-screen warnings and highlighting them, copying these by the same method, and pasting the clopboard contents into a different text editor gave you the tools to do a few quick Replaces in those lines.  You get rid of everything up to and including the word "entry ", meaning the space after entry as well.  Do a Replace All so that it only has to be done once.  Then take everything from the " i386" to the end of the line and either replace it with nothing or delete it with the Del key after highlighting it.  Repeat this last step working with " amd64" instead of " i386".  Now you are about ready to return to the sources.list file.  But not quite.

If you look at sources.list entries and compare them to this second file, you may see entries combined in sources.list that are handled separately in the 2nd file.  in my case, sources showed "main reserved" handled in a single entry, while in the other file, "main" and "reserved" appear on two separate lines.  This meant that by commenting one line in sources.list, I would eliminate two warnings in the 2nd file.  But by already having removed "i386" and "amd64". I had really reduced four warning to one in sources.list.  Just one entry in sources.list was causing my problem.

Finding the problem line was another copy&paste, from 2nd editor to 1st, putting the paste into a search box on the sources.list editor.  It found several possible candidates, that on study, could be told apart to some degree.  For instance, I could ignore lines that began with # were already commented out.  Then anything that said "deb-src" could be ignored, since these are just source files for future recompiles when new releases come out.
That just left the "deb" files to deal with.  But that still left what looked like a couple of candidates, even after I took "reserved" and "main" into account.  How would I know the right one now?

The answer answer was simple:  Comment one of them out by putting at least a # a the front of it.  I put ### as a signature that rhis was a change I was making personally.  If it failed to fix the problem, I could come back, remove the ### from this line, and try one of the other lines instead.  I saved the file but kept the editor open just in case, then went back through the update/upgrade process, which I have down as a script file so that I don't have to type it in over and over again.  No warnings this time.  I got the right line.  So I closed the editors, and that is one more pesky problem dealt with.  I'm marking this thread SOLVED.

By the way, my update and upgrade script files are examples of what you can do if you learn enough about scripting so that you can copy a script into a text editor, save it under a name of your choice where you want to put it, mark it as executable, and possibly use gsettings or dconf-editor to get the File Manager to run it from the GUI.  Otherwise you can use a terminal, type in the path/filename, and hit enter.  Sme results, as long as you select Ask under either gsettings or deconf-editor and always pick "Run in Terminal" as your option.  That's because in many scripts, you are asked for your password, and if you use "Run" with such a script. you won't see the request for password and you won't be able to provide it, so the script hangs.  Besides, with Ask, the middle choice is Display, which actually opens the file in gedit, so you can edit it on the spot if you want or need to.

I will be glad to post the scripts on request.  However, rather than just do it now and be done with it, I need a request because forum staff seems to be of the opinion that scripting is not what the forums are about.  They "jailed" another script that I posted not long ago.  But scripts from me are about helping others get things done so that they don't have to become experts themselves.  I'm not an expert with Linux, bash, scripts, programming overall, but I have been supporting computer systems and users since 1969, and I keep learning as I go.  When I learn something, I look at ways to pass it along to others to make the process of learning less arduous to them.  Scriptiing is one of the better ways of getting this done.  With script being provided, the yser only needs to learn enough to get the script to work, which is easy to do.
                        
What goes into a script is another story.  That is where the expert part fits in.  But with the internet and search engines, you just have to put the need into words and search for answers.  Then anyone can become as expert as they want at almost anything, if they just enough time and effort into it.

---

### Post by vasa1 on 2015-11-05
> **ajgreeny said:**
> Can you please show us the total output in terminal of ```
cat /etc/apt/sources.list
``` and we can then tell you which lines to remove or comment out (add a # at start of line).
Is there some problem in providing the code requested?

---

