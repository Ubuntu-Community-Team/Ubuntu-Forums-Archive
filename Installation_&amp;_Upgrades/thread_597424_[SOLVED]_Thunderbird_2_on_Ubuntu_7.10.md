---
title: "[SOLVED] Thunderbird 2 on Ubuntu 7.10"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by rmhodv on 2007-10-30
I have been trying to install Thunderbird 2 for about 2-3 days now without any luck :(
I have looked on the repositories via System > Administration > Synaptic Package Manager but can't see Thunderbird there.  Please Help

---

### Post by logos34 on 2007-10-30
Do you have all the repos enabled?

Otherwise use [Automatix2]("http://www.getautomatix.com/") to install tbird

---

### Post by timcredible on 2007-10-30
try mozilla-thunderbird.  i use it on 7.10, installed it from synaptic, it works fine, and if i remember correctly, i installed it just using the default repos.  make sure you enable the default repos with Settings->Repositories and make sure they're all checked, except source.

---

### Post by dabang on 2007-10-30
Thunderbird 2 is part of Gutsy. Look [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=thunderbird&searchon=names&subword=1&version=gutsy&release=all").
```
sudo apt-get install thunderbird
```
should do the trick.

---

### Post by rmhodv on 2007-10-30
> **timcredible said:**
> try mozilla-thunderbird.  i use it on 7.10, installed it from synaptic, it works fine, and if i remember correctly, i installed it just using the default repos.  make sure you enable the default repos with Settings->Repositories and make sure they're all checked, except source.

I've tried this, but all I get is 'no package is selected' when I search. I have also made sure that all the repros are enabled except source.

---

### Post by rmhodv on 2007-10-31
> **rmhodv said:**
> I've tried this, but all I get is 'no package is selected' when I search. I have also made sure that all the repros are enabled except source.

Has anyone got any ideas as to what I might be doing wrong?  Like I say I can't even see Thunderbird in the default repos.

When I hit refresh, it gets to 17 of 20, and then presents an error saying that this repro may be out of date, or that their may be something wrong with the network. I can't see this being my end,as I'm connected toi the internet.

---

### Post by louieb on 2007-10-31
Just did a Synaptic search for **thunderbird**.  V2.0.0.8 is in the main repository. Your probably right  about something being wrong with your network. May want to try a different mirror. System>Admin> Software Sources > other.

---

### Post by erginemr on 2007-10-31
Alternatively, you may download and install Thunderbird directly from the following address:
[http://packages.ubuntu.com/gutsy/web/thunderbird](http://packages.ubuntu.com/gutsy/web/thunderbird)

---

### Post by It_Was_Luck on 2007-10-31
Type this in your terminal, this download is for Thunderbird 1.5, but it automatically updates the update to 2.

```
sudo apt-get update && sudo apt-get install mozilla-thunderbird
```

---

### Post by rmhodv on 2007-10-31
Finally I've managed to install Thunderbird from the repos. But this is just the start of my problems.

Now when I try to launch thunderbird, the computer just hangs, and tbird won't run.

Any ideas?

---

### Post by rmhodv on 2007-11-01
> **rmhodv said:**
> Finally I've managed to install Thunderbird from the repos. But this is just the start of my problems.

Now when I try to launch thunderbird, the computer just hangs, and tbird won't run.

Any ideas?


Calling all Ubuntu guru's. Please help.

I'm sure that there is someone out there who knows what's going on with tbird.

---

### Post by rmhodv on 2007-11-01
Anyone.....:(

---

### Post by dabang on 2007-11-01
Try starting thunderbird from a terminal and post the output. Maybe it'll help...

By the way, how did you install thunderbird?

---

### Post by erginemr on 2007-11-01
> **rmhodv said:**
> Anyone.....:(

I have been following your post, but it is really very difficult to say anything. This is apparently a very specific error to your computer. 

You may give more information on which version you installed (1.5, 2.0), how you installed it (via repositories, Debian package form somewhere else, from the source file, or from the binary installer on the Thunderbird's site.

Finally, try thunderbird or mozilla-thunderbird from a virtual terminal to catch the error messages.

If you supply all this info, maybe there will be someone to identify and solve your problem.

Good luck...

EDIT: Sorry, dabang suggested exactly the same. So, I second to his suggestion...

---

### Post by rmhodv on 2007-11-01
> **dabang said:**
> Try starting thunderbird from a terminal and post the output. Maybe it'll help...

By the way, how did you install thunderbird?

> **erginemr said:**
> I have been following your post, but it is really very difficult to say anything. This is apparently a very specific error to your computer. 

You may give more information on which version you installed (1.5, 2.0), how you installed it (via repositories, Debian package form somewhere else, from the source file, or from the binary installer on the Thunderbird's site.

Finally, try thunderbird or mozilla-thunderbird from a virtual terminal to catch the error messages.

If you supply all this info, maybe there will be someone to identify and solve your problem.

Good luck...

EDIT: Sorry, dabang suggested exactly the same. So, I second to his suggestion...

Firstly, thank you both for your speedy response. 

I installed thunderbird from the repositories, I know I had problems, but to overcome this I changed the mirror site to one in the UK (May want to try a different mirror. System>Admin> Software Sources > other.
), and then installed it from the Synaptic Package Manager.

The version I have installed is 2.0.

Also being new to linux and Ubuntu (1 week) how do you try thunderbird or mozilla-thunderbird from a virtual terminal to catch the error messages?

I have installed all this on a brand new laptop. This one. [http://www.novatech.co.uk/novatech/specpage.html?NNB-573](http://www.novatech.co.uk/novatech/specpage.html?NNB-573)

I bought it with No Operating System Installed. :)

Thank you again. Hopefully we can sort this out.

---

### Post by erginemr on 2007-11-01
I hope so. But in any case, don't let such issues turn you away from Linux. In the worst scenario, you can always uninstall Thunderbird and carry on with Evolution, which is also a wonderful e-mail reader and contact manager in its own right. (I am also using Evolution.) And there are other great mail readers such as slypheed and claws mail that you may want to try out.

Speaking of your question, you open up a virtual terminal by the main menu Accessories -> Terminal. You write down mozilla-thunderbird or just thunderbird and see what happens. (I am not sure of which one, I am stuck with a Windows machine now in the office.)

It will crash as it did when you try to run it from the menu, but this time, you will see some error messages on the console. Then, you select all the error messages issued with your mouse, right click, copy and back to Firefox to paste the error message to your post.

That's it...

---

### Post by rmhodv on 2007-11-01
> **erginemr said:**
> I hope so. But in any case, don't let such issues turn you away from Linux. In the worst scenario, you can always uninstall Thunderbird and carry on with Evolution, which is also a wonderful e-mail reader and contact manager in its own right. (I am also using Evolution.) And there are other great mail readers such as slypheed and claws mail that you may want to try out.

Speaking of your question, you open up a virtual terminal by the main menu Accessories -> Terminal. You write down mozilla-thunderbird or just thunderbird and see what happens. (I am not sure of which one, I am stuck with a Windows machine now in the office.)

It will crash as it did when you try to run it from the menu, but this time, you will see some error messages on the console. Then, you select all the error messages issued with your mouse, right click, copy and back to Firefox to paste the error message to your post.

That's it...

I'm also stuck at work at the mo on a Windows machine, but will be indoors at home in about 1.5 ish time. I'll do the above, and keep my finders crossed.

Thank you again. It's cool that there are people in the forum prepared to help. It certainly helps to keep you going.

---

### Post by rmhodv on 2007-11-01
OK, I have just typed Thunderbird into Terminal, and this what I get.

/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Hope this helps with a diagnosis.

---

### Post by erginemr on 2007-11-01
OK. I begin to understand. There is a package installed in Ubuntu: lbstdc++ but that is version 6. You need to install version 5 too, for Thunderbird to work. You can install it  along with ver.6, there is no problem with that. 

Check out the attached screen-shot, give it a try and cross your fingers.

---

### Post by erginemr on 2007-11-01
Alternatively, you may try tricking Thunderbird that libstdc++ ver.5 is installed, by symbolic linking (making a shortcut of, in Windows-speak) libstdc++.so.6 to libstdc++.so.5 with the following command:
"sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5"

Here, "ln" is the command for creating links (shortcuts) of files, "-s" for symbolic linking (there is also hard linking, but that is an advanced topic), first file name is the existing target file, and second file name is the symbolic link file to be created.

This way, you may (or may not, it depends) trick Thunderbird that ver.5 is installed without actually installing the library in question.

EDIT: Sorry, the files were in "/usr/lib", Corrected that mistake...

---

### Post by rmhodv on 2007-11-02
> **erginemr said:**
> OK. I begin to understand. There is a package installed in Ubuntu: lbstdc++ but that is version 6. You need to install version 5 too, for Thunderbird to work. You can install it  along with ver.6, there is no problem with that. 

Check out the attached screen-shot, give it a try and cross your fingers.


Cool. thank you very much.

Thunderbird is working :)

---

### Post by erginemr on 2007-11-02
> **rmhodv said:**
> Cool. thank you very much.

Thunderbird is working :)

Very glad to hear that.

Take care...

---

### Post by rmhodv on 2007-11-02
Thanks again for your help:)

The only thing left to do, which I'm sure I'll be ok with is to get the codecs for the DVD.:popcorn:

---

### Post by erginemr on 2007-11-02
> **rmhodv said:**
> Thanks again for your help:)

The only thing left to do, which I'm sure I'll be ok with is to get the codecs for the DVD.:popcorn:

Oh, that is an easy stuff. I installed totem-xine to watch DVD's which replaced the default totem-gstreamer (same program, but with a xine backend library). I have also installed a second program based on xine, namely Gxine as a backup player.

There is also a libdvdcss2 package to play encripted DVD's, which exists under Medibuntu repository. You may (or may not) need it after the installation of Totem-xine. See if you can play DVD's without it first. To see how you can install it, check out the following thread:
[http://ubuntuforums.org/showthread.php?t=598071](http://ubuntuforums.org/showthread.php?t=598071)

---

### Post by dabang on 2007-11-02
I just wonder why lbstdc5++ wasn't installed as dependency... Must have been a "funny" repository you were using!

For DVD Playback:

```
sudo apt-get install libdvdnav4 libdvdread3
```

If you're running 64bit Ubuntu add

```
sudo apt-get install build-essential debhelper fakeroot
```


To install lbdvdcss (not legal in all countries...) for viewing encrypted DVDs:

```
sudo /usr/share/doc/libdvdread3/installcss.sh
``` (not sure about exact path, running windows right now...)

This will download the libdvdcss package and install it. If you're running 64bit Ubuntu, it'll compile it from source, build the package and install it ( - all automatically). Just as alternative, so you don't need to add extra repositories. To actually view DVDs you may use xine, vlc, etc... as already suggested.

---

