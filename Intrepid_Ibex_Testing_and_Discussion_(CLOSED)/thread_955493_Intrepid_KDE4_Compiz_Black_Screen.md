---
title: "Intrepid KDE4 Compiz Black Screen"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mac.cole on 2008-10-22
Help!!!

Yesterday I turned off my Compiz effects.  Thinking that they weren't designed to function on KDE4.  Before doing so this new beta release was functioning perfectly for my average user purposes. Now, I can log in to the desktop but it is solid black with a mouse pointer that can be controlled.  I assume that everything is functioning behind the black screen because I can even hear the logon.

So far I have:

unsuccesfully searched for a CLI tool to reset the Compiz engine settings (CCSM?) and tried to run a 'compiz-switch', unsuccesfuly from the console.

Succesfully removed, updated, and cleaned prior to reinstalling a fresh compiz/compizconfig-settings-manager/and emerald package but didnt fix the black screen

tried to mv kdeconfig to kdeconfig-old. Which is a generic fix that I read about and can only imagine that it results in the rebuilding of this file with default settings. I dont think that is the name of the file any more with this 8.10 Beta.  Im going to try the same operation on a .kde4 after this post.

I also rewrote a line in systemsetting.conf from windowtransparencyengine=disable to windowtransparencyengine=enable (rough translation). No fix.

What I'd most preffer is a solution that will reset the Compiz settings to their previous functional state but this must be doable in the Console. 

Next Kwin should be able to take the place of compiz but when I run kwin --replace I get a can't connect to xserver message.  Funny because I swear when I exit and shut down I catch a quick glimpse of a kwin shutting down message. So anyway, maybe someone can help me get Kwin going barring resetting Compiz.

Lastly, I would be willing to try putting a different DE next to KDE but only something light like XFCE.  I already tried running sudo apt-get install xubuntu desktop but either I had syntax wrong or didn't have the repository added which I would need a tutorial on.  A new desktop seems like a possibly reckless solution but I dont have all my stuff backed up or else I would just reinstall the whole damn thing with unetbootin.  I'd much rather fix this smartly.

Can anyone offer some suggestions?

---

### Post by mac.cole on 2008-10-24
Renaming the .kde4 file "mv .kde4 .kde4-old(or something)" almost reset the default settings.  Upon reboot a file named .kde was created in the same directory.  At that point the DE was still blacked out upon session login.  However, because the previous config file was named .kde4 and not .kde I surmised that perhaps this is a bug that hasn't been massaged from Intrepid yet.  I.E. it recreated a new config file with the wrong name.  So, I performed one more mv:  "mv .kde .kde4", then I rebooted, and logged into the DE; viola.  Success.  It's very sweet to successfully troubleshoot.  Having to reinstall sucks.  

Keep in mind that this solution resets the desktop environment to it default settings.  No custom background, plasmoid containment, or widgets.  You do have to recreate those, which I have since noticed that my customizations of the desktop itself aren't as reliable and persistent as the settings for the Compiz Fusion engine.  Compiz is slightly more solid.  If you notice that Kwin has taken over mysteriously and Fusion has gone AWOL then "Compiz --replace" is a good command to try.  I've used it several times successfully.

Thanks

---

### Post by ashrack on 2008-10-25
I have the same problem except I never even touched the compiz thing. All I did was install the RC and then updated it and after reboot I have this problem.
Will try your solution now and see how it goes.

---

