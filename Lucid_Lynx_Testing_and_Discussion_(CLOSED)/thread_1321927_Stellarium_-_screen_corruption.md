---
title: "Stellarium - screen corruption"
date: 2009-11-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-11-10
Has anyone tried running Stellarium 0.10.2-1 from the Lucid repositories ?
I've run Stellarium in 9.04 with no problems, but in Lucid the screen doesn't seem to refresh properly, there is nothing shown by default (just a black screen) and the command/help windows don't close when the close (X) is clicked.
Attached is a screenshot.

---

### Post by ranch hand on 2009-11-10
Never heard of it, looks neat.  Down loading now.  Will let you know.

Thanks for letting me know about it.

---

### Post by alphacrucis2 on 2009-11-10
> **Kevbert said:**
> Has anyone tried running Stellarium 0.10.2-1 from the Lucid repositories ?
I've run Stellarium in 9.04 with no problems, but in Lucid the screen doesn't seem to refresh properly, there is nothing shown by default (just a black screen) and the command/help windows don't close when the close (X) is clicked.
Attached is a screenshot.

It is an OpenGL app so it could be a video driver problem. It runs fine for me under 9.10 with the dreaded proprietary fglrx driver. I can't test it on my Lucid box right now as I am at a different location.

---

### Post by alphacrucis2 on 2009-11-10
> **ranch hand said:**
> Never heard of it, looks neat.  Down loading now.  Will let you know.

Thanks for letting me know about it.

It's a great tool for stargazers like me.:D

---

### Post by ranch hand on 2009-11-10
I got involved in too much stuff today to try it and now I am back on 9.04.  I will give it a whack in the morning.

All I run is the generic driver.  My ATI card is not well treated any other way.

---

### Post by alphacrucis2 on 2009-11-10
Just a thought for the OP. Try out google earth and see if that has similar problems.

---

### Post by ronacc on 2009-11-11
runs fine here with both the default video driver and the repo Nvidia 185.18.36   . It is very sluggish with the defaule ( vesa ? ) driver but no screen corruption . satisfyingly snappy with the nvidia driver .

---

### Post by ronacc on 2009-11-11
@ ranch hand   there are several astronomy apps in the repos , celestia is also nice .

---

### Post by ranch hand on 2009-11-11
I have heard of that one, think I took a look once.

I downloaded the one in question just to try it and see if it worked.  The way I am set up this time lets me play more AND get more work done boinc wise.

Another advantage of this set up is that boinc is running the way it does here on my usual OS.  Cpus at 100% most of the time.  Lounge Lizard had better be up to it or it WILL show.

This app is a video using app too so it aught to actually call on a cpu at least a little.

---

### Post by ronacc on 2009-11-11
boinc is designed not to slow down your system , it may use 100% cpu but it only takes what isn't needed by something else and it releases back cpu when something else needs it , it runs at a high "nice" setting .

---

### Post by Kevbert on 2009-11-11
Just checked the video driver (for my Nvidia 7600 GS) and I've found that the Nvidia 185.18.36 repo driver may be the problem as I'm using 180.44 in 9.04. 
In 9.04 I can even use BOINC running in the background (always active) with no problems.
I've raised a [[COLOR="Red"]bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/480553") on this.

---

### Post by ronacc on 2009-11-11
hmm , strange , last night I was not getting the corruption with the 185.18.36 driver , this morning I installed the 190.42 driver to try that , it gave the corruption so I reverted to 185.18.36 and now it is giving the corruption.

---

### Post by ranch hand on 2009-11-11
That depends on how you set the power preferences.  I have them set so that 9.04 is riding the edge of the catastrophy curve.  So far the Stoned Lizard is holding up better than my usual 9.04.

Back to this stellarium.  I pulled it up and yes there was a blank, black screen.  When the pointer wandered down in the lower left there was a change.  This has to be the control panel, couldn't read a thing.   Looked like several words stacked or something where there was text.  couldn't really make out what the buttons were either as they were very blurry.  There was an identifiable big red button that I was glad worked to kill this bugger.

I am running on the generic drivers, haven't even bothered to look to see if something is available.  I may check it later if there is some news of ATI expanded support.

---

### Post by Kevbert on 2009-11-11
> **ranch hand said:**
> 

Back to this stellarium.  I pulled it up and yes there was a blank, black screen.  When the pointer wandered down in the lower left there was a change.  This has to be the control panel, couldn't read a thing.   Looked like several words stacked or something where there was text.  couldn't really make out what the buttons were either as they were very blurry.  There was an identifiable big red button that I was glad worked to kill this bugger.

I am running on the generic drivers, haven't even bothered to look to see if something is available.  I may check it later if there is some news of ATI expanded support.

So you're getting the same problems with an ATI card by the sound of it ? I thought it was the Nvidia driver. Tomorrow I may try transferring my Stellarium package from 9.04 to 10.04 (same version), just to see if it is the package that's somehow been corrupted. I doubt it though, as I've had video corruption, on a games package as well.

---

### Post by ranch hand on 2009-11-11
Yuppers, Radeon HD 2400 Pro.

---

### Post by ronacc on 2009-11-11
just for grins try starting stellarium from a terminal and see what errors it gives . I removed the repo stellarium and built from source to see if that helped , it didn't . I did find out in the process that stellarium is built against QT not GTK so that may be the problem , it may run ok on kubuntu but I haven't got a kubuntu install to test it on right now . the error I get when I run it from term is ```
StelAppGraphicsScene: drawBackground needs a QGLWidget to be set as viewport on the graphics view
``` repeated many many times .

---

### Post by ronacc on 2009-11-12
so much for that idea , I installed kubuntu 9.10 changed sources and updated , before update no corruption , after update corruption . So it isn't because stellarium is built against QT .It's not the drivers , it does it with both ati and nvidia and I get the same errors starting from term in Kubuntu as in gnome , it must be something about the version of opengl in lucid that it doesn't like .

---

### Post by Kevbert on 2009-11-12
Please post a comment/confirm [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/480553"). I've mentioned that it's not the nvidia driver at fault.

Edit: It could be any one of the QT libraries as they've all been updated...

---

### Post by ronacc on 2009-11-12
confirmed your bug and added comment .

---

### Post by BrMBr on 2009-11-12
That's sad!

Using Intel graphics here. Google Earth works perfectly, but take a look of what happens with Stellarium... :(

Edit: bug reported [here]("https://bugs.launchpad.net/stellarium/+bug/426417?comments=all").

---

### Post by Kevbert on 2009-11-13
Thanks ronacc.
BrMBr thanks for the link. It works fine for me on 9.04 but not 10.04. It must be an updated library file. I'll add a comment to your reference bug report (which is Intel specific).
Someone has suggested int may be a problem that occurs only when running compiz, but if I turn off compiz I still get the same problem.

---

### Post by ranch hand on 2009-11-13
I found this interesting;

[http://ubuntuforums.org/showthread.php?t=1324706](http://ubuntuforums.org/showthread.php?t=1324706)

---

### Post by ronacc on 2009-11-13
@ kevbert   I notice that your bug has the nvidia graphics driver as the package that it is against , I think you need to change that to stellarium since the corruption occurs with ati and intel cards also .

---

### Post by Kevbert on 2009-11-13
> **ronacc said:**
> @ kevbert   I notice that your bug has the nvidia graphics driver as the package that it is against , I think you need to change that to stellarium since the corruption occurs with ati and intel cards also .

I wasn't sure how to change it at the time, but now I've changed it to Stellarium.  I still don't think that this package is the problem, but instead caused by a change in the opengl drivers as the exact same version of Stellarium works fine for me on 9.04. I'm going to raise another video bug on another package shortly.

Edit: I've raised a new bug on ace-of-penguins via apport (thanks ranch hand for that hint). The bug is [[COLOR="Red"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ace-of-penguins/+bug/482225"), please confirm.
Another one. Has anyone got alarm-clock to work ?

---

### Post by ronacc on 2009-11-13
I agree that the "bug" is probably caused by the way that function is called in the new opengl , let the devs figure out where to do the adjusting , in stellarium or opengl . I was just concerned that by it being blamed on the Nvidia driver they would be looking in the wrong direction .

---

### Post by crchtiger on 2009-11-15
> **BrMBr said:**
> That's sad!

Using Intel graphics here. Google Earth works perfectly, but take a look of what happens with Stellarium... :(

Edit: bug reported [here]("https://bugs.launchpad.net/stellarium/+bug/426417?comments=all").


same problem here


00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by antony_css on 2009-11-27
[http://www.stellarium.org/wiki/index.php/Known_issues_with_video_drivers](http://www.stellarium.org/wiki/index.php/Known_issues_with_video_drivers)

---

### Post by zenarcher on 2009-11-27
> **alphacrucis2 said:**
> Just a thought for the OP. Try out google earth and see if that has similar problems.

Same corruption here with Stellarium, but also Googleearth working fine.

Cheers,
zenarcher

---

### Post by Davidmcoop on 2009-11-27
I love this app but the help menus just come up as fuzzy blocks which I can't read. I haven't had the time to investigate further

---

### Post by alsnowdon on 2009-12-11
Stellarium is aware of this bug:
[https://bugs.launchpad.net/stellarium/+bug/426417](https://bugs.launchpad.net/stellarium/+bug/426417)
I have the same problem with a Lenovo Y430 Intel Mobile 4 Series 1280x800
Windows7 version runs fine, and Linux Mint 7 did, too.

---

### Post by bhaverkamp on 2009-12-11
Still working fine for me.... 9.10 hpdv9000

---

### Post by Kevbert on 2009-12-11
> **alsnowdon said:**
> Stellarium is aware of this bug:
[https://bugs.launchpad.net/stellarium/+bug/426417](https://bugs.launchpad.net/stellarium/+bug/426417)
I have the same problem with a Lenovo Y430 Intel Mobile 4 Series 1280x800
Windows7 version runs fine, and Linux Mint 7 did, too.

That bug is specific to Intel, but it also occurs on ATI and Nvidia for Ubuntu 10.04, which is reported here:
[https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/480553](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/480553)

---

### Post by Kevbert on 2010-02-18
The new version of Stellarium 0.10.3 resolves my display problems. It's not yet available in the standard repos but is in [[COLOR="Red"]Scott Howard's PPA[/COLOR]]("https://launchpad.net/~showard314/+archive/ppa").

---

### Post by Giwex on 2010-02-22
Latest update of LL (official repositories) brought 10.3 of Stellarium and the problem is finally gone :D

---

### Post by Kevbert on 2010-02-22
Yup 0.10.3 in the repos, but there's a newer version 0.10.4 which is to be made available by the developer which resolves some bugs.

---

### Post by snahrck on 2010-03-14
Nice, but how to update it to 10.3 or 10.4 in karmic?

---

