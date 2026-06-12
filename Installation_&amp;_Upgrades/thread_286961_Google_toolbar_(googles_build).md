---
title: "Google toolbar (googles build)"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by brad1138 on 2006-10-28
I just installed 6.06 then upgraded to 6.10. The first thing I tried to do after that was install the Google Toolbar from Google. It said it wasn't compatible with my build of FF (2.0). I don't know if it is FF 2.0 or UBUNTU that is causing the problem. Google does say it requires "Red Hat Linux". I know there is a FF extension not made by Google but I like Googles version best. Any ideas?

Thanks,
Brad

---

### Post by msak007 on 2006-10-28
I had the same problem and was hoping someone found a real solution. I googled the error and found [this]("http://groups.google.com/group/FFToolbar-Group-Bugs/browse_thread/thread/3d48b5cf7413904f") post on Google Groups which has a hackish fix for it, maybe it'll help you. I haven't tried it yet so I can't tell you if it works, but it seems to be a problem specific to Firefox 2 on Edgy.

EDIT: If you haven't encountered the error or aren't sure what it says, when trying to install the extension it aborts with the error:
```

"Google Toolbar for Firefox" could not be installed because it is not compatible with your Firefox build type (linux-gnu_x86-gcc3). Please contact the author of this item about the problem". 
```I've included a screenshot to verify that the right extension is being installed with the error message included.

---

### Post by rfruth on 2006-10-28
I installed the toolbar when I used Breezy & Fx ver 1.5, had to jump through hoops (not too bad) never did get the Autofill option to work :mad: but everthing else is fine, upgraded to Edgy the other day and the Google toolbar works like it always has (thank goodness)

---

### Post by msak007 on 2006-10-28
I didn't have the problem installing the extension in Dapper, and when I dist-upgraded from Dapper --> Edgy the extension was updated to work with FF 2.0 Bon Echo. I reformatted and installed from scratch after Edgy final was released, and now trying to install the extension errors out with FF 2.0 Final

---

### Post by brad1138 on 2006-10-28
Well I am glad to know I am not alone, I guess :-k  . msak007 that is exactly what I ran into. I dont really want to reinstall 6.06, add toolbar, then upgrade to 6.10 again, think I'll wait, see if it is soon fixed (6.101 maybe :))

Thanks,
Brad

---

### Post by brad1138 on 2006-10-29
Just refreshing this, maybe a few days after 6.10 is out more people will have experienced this problem.

Brad

---

### Post by ioannis on 2006-10-30
I ran into the same problem when I did a fresh install of edgy. I found the same solution posted in Google pointed to by msak007 above, and I tried it. Took 1 minute and worked perfectly. The hackish fix is simple and doesn't seem that it would create any problems, so for people that like having Google Toolbar, I definitely recommend it.

---

### Post by avryhof on 2006-10-31
Install my package...

I didn't follow the hack listed on google groups, I just changed the target to linux-gnu_x86-gcc3 other than that, it is verbatim to the official package.

My package retains the digital signature and everything.

[http://www.vryhofresearch.com/software/google-toolbar-edgy.xpi]("http://www.vryhofresearch.com/software/google-toolbar-edgy.xpi")

Enjoy!
:D

---

### Post by brad1138 on 2006-10-31
> **avryhof said:**
> Install my package...

I didn't follow the hack listed on google groups, I just changed the target to linux-gnu_x86-gcc3 other than that, it is verbatim to the official package.

My package retains the digital signature and everything.

[http://www.vryhofresearch.com/software/google-toolbar-edgy.xpi]("http://www.vryhofresearch.com/software/google-toolbar-edgy.xpi")

Enjoy!
:D

Thank you but I am a bit of a noob with Ubuntu/Linux. What do you mean "changed the target" also after I dl your file, how do I install it?

Thanks,
Brad

---

### Post by avryhof on 2006-10-31
XPI Files can be extracted as ZIP files, once this is done, you have access to the entire directory structure.  

Within the XPI is a file called install.rdf tht specifies how the installation package works.

In that file is a line that reads
<em:targetPlatform>Linux</em:targetPlatform>

I just changed "Linux" to "linux-gnu_x86-gcc3" zipped it back up, renamed it to an xpi and it installed just fine.

As for the answer to your second question.  Save it to your desktop or home directory, bring up a firefox window, and just drag the XPI into the window... it will install.

I'll make the link on my website so it can be installed from there...didn't have much time this morning.

---

### Post by brad1138 on 2006-10-31
Thanks avryhof, your good. Worked like a charm :D

---

### Post by avryhof on 2006-10-31
Ok, I made the link on my site so it will do automatic installation.  Unfortunately, I can't make a link in the forum do it so...without further dely... for those who dont want to download the XPI and drag it into Firefox

1. Go to [http://www.vryhofresearch.com/]("http://www.vryhofresearch.com/")
2. Click on Software in the menu on the left hand side
3. Scroll down to Firefox Extensions
4. Click the link for google-toolbar-edgy

That's it.. aside from FF asking you to setup my site as a trusted installation location, it should be simple.

---

### Post by msak007 on 2006-10-31
Thanks for the updated XPI avryhof as I'm sure many people will run into this issue and most won't want to hack the file manually like we did, but this is still a bug that should be reported. Who it should be reported to I'm not sure (Google? Ubuntu? Both?), so if anyone wants to report it or even tell me how to report the bug I'll do it myself.

---

### Post by avryhof on 2006-11-01
Thanks.  I reported it to Google.  However, in their defence.... they only officially support Red Hat 9.0 ... so it's not really a bug.

I suggested that they should have an area for unofficial, or user contributed XPI files of the Toolbar...I'm sure the community at large would gladly support that solution.

On the other hand... maybe the fixed package should be added to the Universe repository... but I'm not a member of the developer mailing list, so I can't suggest the package.

---

### Post by sam81 on 2006-11-02
I installed the toolbar, but had some random firefox crashes (actually freezes) after, and now I have uninstalled it. I think it might not be really compatible with the firefox version shipped with Edgy. Has any of you had similar problems?

---

### Post by avryhof on 2006-11-02
No problems here... the only time FF2 has had trouble since I installed Edgy was when I tried the GrayModern2 theme, and switching to another theme solved that issue.

---

### Post by johnny9794 on 2006-11-03
ok i think google is full of sh*t and maybe not but in ubuntu 6.06.1 there was the 1.5 version of firefox ok? So I installed google toolbar for the 1.5 on 1.5 Firefox and all my little add-ons ect. Then i wanted to put firefox 2.0 on and so i did by following this tut [http://ubuntuforums.org/showthread.php?t=283965&highlight=firefox+2.0+ubuntu+6.06.1](http://ubuntuforums.org/showthread.php?t=283965&highlight=firefox+2.0+ubuntu+6.06.1)

after i loaded up 2.0, it imported all my addons "including" the google toolbar that is for firefox 1.5. and the toolbar worked great and had no problems.

But i just installed edgy and I just want to thank Avryhof for your support :).


Thanx google-toolbar-edgy.xpi works GREAT!!!

---

### Post by IanVaughan on 2006-11-23
Its very odd, I installed the toolbar in FF1.5 when using Dapper.
Then I upgraded to Edgy (include FF2.0) and the toolbar was still there no probs.

But I've just done a new install of Edgy, and tried the install the Toolbar, and hit this brickwall!

(I installed the file from the link in one of the first posts of this thread and it installed and is working fine!)

---

### Post by msak007 on 2006-11-23
> **IanVaughan said:**
> Its very odd, I installed the toolbar in FF1.5 when using Dapper.
Then I upgraded to Edgy (include FF2.0) and the toolbar was still there no probs.

But I've just done a new install of Edgy, and tried the install the Toolbar, and hit this brickwall!

(I installed the file from the link in one of the first posts of this thread and it installed and is working fine!)
That's the exact problem - the toolbar seems to have no problems if you install it in 1.5 and then upgrade to 2. But if you do a fresh install of Ubuntu's FF2 and then try to install the toolbar, you get the error.

---

### Post by nibi on 2006-12-18
I encountered the same problem when installing google toolbar on ff2 on kubuntu edgy. Its interesting to note that the beta version installs fine, doesn't give this incompatibility message.

---

### Post by mahiyar on 2006-12-28
Thanks a lot for these forums, most (most) of my problems are resolved here. Well installing google toolbar is one more tick to my to do list, bringing me that much nearer to completely discarding Windows.

---

