---
title: "How to install Ruby plugin for Eclipse"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by vhof on 2007-11-10
Hi folks,
just wanted to share how to install it, since it's simple, but there's a tiny catch..

But before, you need the Eclipse IDE of course, so go and check it in Synaptic, if you didn't do that before :) Also, it's nice to install CDT (c++ plugin) PyDev (Python plugin) etc. from Synaptic, but since Ruby isn't there, follow me.

Ok, right from [this]("https://help.ubuntu.com/community/EclipseIDE") page I extracted the needed info for you:


[COLOR="DarkRed"]To install RDT:

    *  Open Eclipse and click on Help -> Software Updates -> Find and Install. This will bring up a dialog allowing you to choose from updates to currently installed features or finding new features to install.

    *  Choose Search for new features to install -> Next.
    
    *  Click the New Remote Site button. A dialog opens allowing you to input the location of the plugin you wish to install.
    
    *  In the Name: box place RDT (or Ruby if that's more descriptive).
    

    *  In URL: type [http://updatesite.rubypeople.org/release](http://updatesite.rubypeople.org/release). Then click Ok.


    *  You should now see RDT in the list of Sites to include in search: box.
    

    *  Click on Finish
    

    *  A dialog to install RDT should now appear. Click the checkbox next to RDT in the Select features to install: area.
    

    *  Click Next -> Accept the License Agreement -> Next -> Finish
    

    *  A Feature Verification dialog will appear click Install All.
    

    *  After the plugin installs click Yes to restart Eclipse.
[/COLOR]


Now you may encounter the following message or similar: 

[COLOR="DarkRed"]Ruby Mylyn Connector Feature (Optional) (0.9.1.200710312030NGT) requires feature "org.eclipse.mylyn.context_feature (2.0.0.v20070628-1000)", or later version.
[/COLOR]

From [this link]("http://www.aptana.com/forums/viewtopic.php?p=12972&sid=6223e9e9a588ebefa07a96d04218b4e4") - just uncheck Mylyn and continue the installation (click Finish). 

Hope this helps.

---

### Post by ineiti on 2007-12-11
Hi,

I just had the same problem. Obviously it's the RDT that has two parts. Just uncheck the "Ruby Integration" (you can see that after clicking on the black triangle) and off you go.

Now I'm checking whether I can use it again like it worked under edgy...

Ineiti

---

