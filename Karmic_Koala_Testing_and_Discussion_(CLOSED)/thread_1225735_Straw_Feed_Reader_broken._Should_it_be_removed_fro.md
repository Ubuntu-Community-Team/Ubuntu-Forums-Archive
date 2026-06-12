---
title: "Straw Feed Reader broken. Should it be removed from repositories?"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bornagainpenguin on 2009-07-28
Straw feed reader hasn't worked since Ubuntu Intrepid Ibex 8.10, should it be included in the repositories for Karmic if it still hasn't been fixed by that point?  Why would you want to include a known broken package in a new release?

--bornagainpenguin

---

### Post by wayne_cat on 2009-07-28
> **bornagainpenguin said:**
> Straw feed reader hasn't worked since Ubuntu Intrepid Ibex 8.10, should it be included in the repositories for Karmic if it still hasn't been fixed by that point?  Why would you want to include a known broken package in a new release?

--bornagainpenguin


well ... from the blog:

[http://strawreader.wordpress.com/](http://strawreader.wordpress.com/)

```
This update is triggered by bornagainpenguin’s comment in the last blog entry
where he asks “Straw is dead, isn’t it?”.
Yes, I broke my own promises on delivering the release.
Yes, there is very little development activity.
I don’t want to say that the project is dead even if this is how it looks like to the 
outside world. Ideas are there, even the code is partly there (I still use Straw as my
primary and only news reader – it’s been over a year and a half now I think).
Unfortunately, the time to develop is not there…

```+1

---

### Post by bornagainpenguin on 2009-08-05
Yes, I am aware of the developer's message on the blog.  I did instigate it via my comments on the blog after all...

My point is still valid though--we have an application that no longer works and does not seem to be actively developed in the repositories.  Does it make sense to keep this application in the Ubuntu repositories when it is known to be broken?  I think it gives a black eye to the distro for a user to install an app in the repositories and have it not work, only to be told by others when he or she asks about it this is a known problem and no attempts are being made to fix the situation.

--bornagainpenguin

---

### Post by castrojo on 2009-08-05
Please file a bug to have it removed (explain why like you did here) and subscribe "ubuntu-archive" to the bug.

---

### Post by bornagainpenguin on 2009-08-05
> **whiprush said:**
> Please file a bug to have it removed (explain why like you did here) and subscribe "ubuntu-archive" to the bug.

Bug submitted [here](https://bugs.launchpad.net/ubuntu/+source/straw/+bug/409387)

How do I subscribe "ubuntu-archive" to the bug?

--bornagainpenguin

---

### Post by zekopeko on 2009-08-05
> **bornagainpenguin said:**
> Bug submitted [here](https://bugs.launchpad.net/ubuntu/+source/straw/+bug/409387)

How do I subscribe "ubuntu-archive" to the bug?

--bornagainpenguin

"Subscribe someone else" button on the right?

---

### Post by bornagainpenguin on 2009-08-05
> **zekopeko said:**
> "Subscribe someone else" button on the right?

doh! I saw that but wasn't really sure if that was it or not.  Okay then, all done, except for finding a nice corner to cry over losing one of my favorite apps...

--bornagainpenguin

---

### Post by zekopeko on 2009-08-05
Well is there an error? Perhaps it's something trivial.

---

### Post by bornagainpenguin on 2009-08-05
> **zekopeko said:**
> Well is there an error? Perhaps it's something trivial.

BWAHAHAHAHAHAHAHAHA!  You're joking right?  I've been trying to get help for this ever since Jaunty came out!

See here for my first attempt to get help: [http://ubuntuforums.org/showthread.php?t=1140811](http://ubuntuforums.org/showthread.php?t=1140811)

See here for more recent attempts: [http://ubuntuforums.org/showthread.php?t=1186595](http://ubuntuforums.org/showthread.php?t=1186595)

No one seems to know how to fix the situation.  I can only presume there has been some kind of library changes since Intrepid that are breaking Straw in Jaunty and Karmic, since these errors are happening across distributions (I get the same errors in Fedora).  I suspect it has to do with either a change in Python versions or something to do with the network manager, but I lack the ability to know any more than that.

If you think you can get me up and running again with Straw, I'd be most appreciative!

Here's the error:

```
strawdbus.py:69:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 7 matched rules; type="method_call", sender=":1.61" (uid=1000 pid=5778 comm="/usr/bin/python /usr/bin/straw ") interface="(unset)" member="state" error name="(unset)" requested_reply=0 destination=":1.11" (uid=0 pid=2879 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
```

AFarris01 did some looking into the situation, you might find his preliminaries useful, so go down to post [ten](http://ubuntuforums.org/showpost.php?p=7595418&postcount=10) in the second thread listed and the [second page](http://ubuntuforums.org/showpost.php?p=7595621&postcount=11) to see if any of what he did helps you figure things out.

Thanks!  I appreciate your willingness to look into the situation and apologize for my bitterness.

--bornagainpenguin

---

### Post by bcat on 2009-08-05
I don't use Straw, but maybe I can help you anyway. I ran in to the same error a couple months ago when I was writing a Python script to run shell commands when NetworkManager changed state. It seems that at some point (probably when NM 0.7 was released) the NM D-Bus interface was changed in a way that broke old code that tried to get the current NetworkManager state value. I just looked at the file where you're getting an error, and I think the fix I used might also work here.

Edit /usr/lib/straw/straw/strawdbus.py and change this:

```
                # don't touch offline if it has been previously set.
                if not Config.get_instance().offline:
                        nl.set_state(proxy_obj.state())
```

to this:

```
                # don't touch offline if it has been previously set.
                if not Config.get_instance().offline:
                        nm_props = dbus.Interface(proxy_obj, dbus.PROPERTIES_IFACE)
                        nm_state = nm_props.get(NetworkListener.SERVICE_NAME, "State")
                        nl.set_state(nm_state)
```

And let me know what happens. I'm sorry I don't have time to test it myself, but hopefully this will solve your problem.

---

### Post by bornagainpenguin on 2009-08-05
> **bcat said:**
> I don't use Straw, but maybe I can help you anyway. I ran in to the same error a couple months ago when I was writing a Python script to run shell commands when NetworkManager changed state. It seems that at some point (probably when NM 0.7 was released) the NM D-Bus interface was changed in a way that broke old code that tried to get the current NetworkManager state value. I just looked at the file where you're getting an error, and I think the fix I used might also work here.

I won't be able to test this out today--too much stuff to do and I'm running out of time.  I'll give it a shot tomorrow and report back.  If this works, what do we need to do to get it sent out to everyone?

--bornagainpenguin

---

### Post by 23meg on 2009-08-05
> **bornagainpenguin said:**
>   If this works, what do we need to do to get it sent out to everyone?

Submit a patch. A [debdiff]("https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff") for Ubuntu, and a regular diff output for upstream. Let me know if it works and you need help with the patch.

---

### Post by caryb on 2009-08-05
> **whiprush said:**
> Please file a bug to have it removed (explain why like you did here) and subscribe "ubuntu-archive" to the bug.

whiprush, is it possible to have a place to subscribe to dead unsupported or just 1/2 baked packeges? 1 that comes to mind for me is lemonpos 7 it is not installable. I think launchpad is getting choked with bug reports on active broken packages I feel a place to suggest obsolete unmaintained packages would be good. As part of the process a email can be shot off to the devs or maintainers of the offending program/package giving them the chance to repair within a timespan or have it removed from the Ubuntu repo's



2c Cary

---

### Post by bornagainpenguin on 2009-08-06
> **bcat said:**
> Edit /usr/lib/straw/straw/strawdbus.py and change this:

```
                # don't touch offline if it has been previously set.
                if not Config.get_instance().offline:
                        nl.set_state(proxy_obj.state())
```

to this:

```
                # don't touch offline if it has been previously set.
                if not Config.get_instance().offline:
                        nm_props = dbus.Interface(proxy_obj, dbus.PROPERTIES_IFACE)
                        nm_state = nm_props.get(NetworkListener.SERVICE_NAME, "State")
                        nl.set_state(nm_state)
```

And let me know what happens. I'm sorry I don't have time to test it myself, but hopefully this will solve your problem.

Okay, I did this (using LinuxMint 7, which is based on Jaunty) and the program seems to work **much** better, but there is still an error message which may or may not be important:

```
strawdbus.py:71:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.UnknownMethod: Method "get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
```

Any idea what that means and wherter or not it needs to be fixed?  Thanks in advance!  This is the best I've seen the program perform yet on a more recent version of Linux!

--bornagainpenguin

---

### Post by castrojo on 2009-08-07
> **caryb said:**
> whiprush, is it possible to have a place to subscribe to dead unsupported or just 1/2 baked packeges?

Maybe something like when you file a bug you add a special tag or something in launchpad so people can just look for dead stuff? Sounds like a good idea, feel free to post it on ubuntu-devel!

---

### Post by bcat on 2009-08-07
> **bornagainpenguin said:**
> Okay, I did this (using LinuxMint 7, which is based on Jaunty) and the program seems to work **much** better, but there is still an error message which may or may not be important:

```
strawdbus.py:71:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.UnknownMethod: Method "get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist
```

Any idea what that means and wherter or not it needs to be fixed?  Thanks in advance!  This is the best I've seen the program perform yet on a more recent version of Linux!

--bornagainpenguin

Oh shoot, it looks like I made a dumb mistake when I was retyping the code. It should be "nm_props.Get" with a capital "G", not "nm_props.get" with a lowercase "g". The final code should look like this:

```
                # don't touch offline if it has been previously set.
                if not Config.get_instance().offline:
                        nm_props = dbus.Interface(proxy_obj, dbus.PROPERTIES_IFACE)
                        nm_state = nm_props.Get(NetworkListener.SERVICE_NAME, "State")
                        nl.set_state(nm_state)
```

---

### Post by bornagainpenguin on 2009-08-10
> **bcat said:**
> Oh shoot, it looks like I made a dumb mistake when I was retyping the code. It should be "nm_props.Get" with a capital "G", not "nm_props.get" with a lowercase "g". The final code should look like this:

```
                # don't touch offline if it has been previously set.
                if not Config.get_instance().offline:
                        nm_props = dbus.Interface(proxy_obj, dbus.PROPERTIES_IFACE)
                        nm_state = nm_props.Get(NetworkListener.SERVICE_NAME, "State")
                        nl.set_state(nm_state)
```

It's just not happening.  I tried this both on Mint Linux 7 and on Jaunty (9.04) and in both cases what happened was no errors being shown in terminal, but also no updating of my feeds.  Straw grabbed the list of articles per feed (indicated by the number of articles), but failed to download any actual content it appears, since clicking on the thread did not provide even a title list.  

Unless someone knows a way to force the application to give off detailed messages about what it's doing (or not doing as it may be in this case) I'm stuck.  Thanks for your help, hopefully I'll be able to find something else that will allow me to do offline feeds (with embedded images showing, etc) before I have no choice but to roll back to WinXP and use Feed Demon for my needs.

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-08-10
Oh and bcat?  Thanks for taking the time here to try and help me with my problem I'm having with Straw.  I appreciate the effort.

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-08-22
/forlorn bump

---

### Post by bornagainpenguin on 2009-10-20
Now that Karmic is around the corner can anyone recommend me a replacement for Straw?

--bornagainpenguin

---

### Post by Keyper7 on 2009-10-20
> **bornagainpenguin said:**
> Now that Karmic is around the corner can anyone recommend me a replacement for Straw?

I like Liferea.

---

### Post by bornagainpenguin on 2009-10-20
> **Keyper7 said:**
> I like Liferea.

I suppose I should have been more specific.  Could you recommend me a feed reader that does **true** offline, text *and* images?  There was supposedly a filter that would allow Liferea to do this but I was never ablke to get it to work.

See: [http://ubuntuforums.org/showthread.php?t=1251672](http://ubuntuforums.org/showthread.php?t=1251672)

Can you make the filter script work?  I've had no luck with it.

--bornagainpenguin

PS: Thank you for the suggestion, I *do* appreciate it.

---

