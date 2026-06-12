---
title: "Software&amp;updates"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2014-09-04
Do I need to download "Source Code"? can I uncheck from this dialogue box?


[IMG]http://i.imgur.com/YVGg8sF.png[/IMG]

---

### Post by slickymaster on 2014-09-04
You'll find the answer for your question in [this thread]("http://ubuntuforums.org/showthread.php?t=2241622").

---

### Post by mayagrafix on 2014-09-04
Thank you very much for the responce. However, Re: Why are the source repositories enabled by default?  is not what I want ot know. I want to uncheck "source code" from automatic downloads because is (i think) unncessary.

---

### Post by ibjsb4 on 2014-09-04
Looks like you have source code unchecked.

To manually do it:
```
gksudo gedit /etc/apt/sources.list
```
And put a hash mark (#) in front of them.

Then update

---

### Post by sjeanr on 2014-09-04
You don't need to have "Source code"! On your posted image it is already not selected. By default "Source code" is not selected.

---

### Post by vasa1 on 2014-09-05
> **slickymaster said:**
> You'll find the answer for your question in [this thread]("http://ubuntuforums.org/showthread.php?t=2241622").And this post in that thread has two useful links: [http://ubuntuforums.org/showthread.php?t=2241622&p=13114611#post13114611](http://ubuntuforums.org/showthread.php?t=2241622&p=13114611#post13114611)

---

### Post by deadflowr on 2014-09-05
> **sjeanr said:**
> You don't need to have "Source code"! On your posted image it is already not selected. By default "Source code" is not selected.

That's not exactly correct.
That - symbol means it is enabled.

To the op, simply click on that box next to source code, it'll ask for your password, then it'll leave you an unchecked box.(Totally empty)
Then it'll ask to reload when you close the software sources.
When all is done the sources.list file found in /etc/apt/sources.list, should have either no entries for deb-src anymore, or all will be #commented out.

And, yes, no harm will come from disabling them.

---

### Post by ibjsb4 on 2014-09-05
> **deadflowr said:**
> That's not exactly correct.
That - symbol means it is enabled.

That is just plain sneaky.

---

### Post by vasa1 on 2014-09-05
Mine is simpler and, dare I say, "intuitive": [http://ubuntuforums.org/attachment.php?attachmentid=255891&d=1409191632](http://ubuntuforums.org/attachment.php?attachmentid=255891&d=1409191632)

---

