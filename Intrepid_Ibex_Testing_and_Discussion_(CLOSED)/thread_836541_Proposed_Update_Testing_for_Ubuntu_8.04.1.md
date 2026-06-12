---
title: "Proposed Update Testing for Ubuntu 8.04.1"
date: 2008-06-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 23meg on 2008-06-21
As most of you already know, the Ubuntu 8.04 release is soon to get an updated CD image with all fixes published so far already applied. This is going to be labeled Ubuntu 8.04.1, similar to the maintenance respins of Ubuntu 6.06 (Dapper Drake), and will be out on July 3rd.

Fixes targeted for 8.04.1 first go into the *hardy-proposed* repository, which is the repository used for testing [stable release updates]("https://wiki.ubuntu.com/StableReleaseUpdates") before they are published to *hardy-updates*. By following the steps below, you can test fixes for known issues to be fixed with stable release updates. We're [already in freeze]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-June/000439.html") for 8.04.1 now, and new fixes will need to go through the release team for approval, so the faster you can provide verification, the better.

Just in case it's not obvious enough: you have to do this in Hardy, not Intrepid. The reason I'm posting this in this forum is that most people who frequent it have also tested Hardy and are familiar with the outstanding bugs, and can be assumed to be capable of doing this kind of testing. 

[list=1]
[*] Enable *hardy-proposed* by ticking the "Proposed updates" box on the "Updates" tab in System -> Administration -> Software Sources.

[IMG]http://i30.tinypic.com/4gruhk.png[/IMG]


[*] [Apport]("https://wiki.ubuntu.com/Apport") is disabled in stable releases. It's recommended that you manually enable it when testing proposed updates, so that crash reports can be collected more efficiently. To enable it, first issue

```
gconftool -s /apps/update-notifier/show_apport_crashes --type bool true 
```

and then edit /etc/default/apport 

```
sudo nano /etc/default/apport
```

and change "enabled" to "1". Once Apport is enabled, start the process with 

```
sudo /etc/init.d/apport start
```

To test that Apport is now running, enter the following command to cause a simple crash and generate a crash file in /var/crash: 

```
sh -c 'kill -SEGV $$'
```

In the event that you end up reporting a crash about a proposed package, please add the **proposed-pkg** tag to the bug so that it can be distinguished from other crash reports. 


[*] To register the fact that you are running *hardy-proposed*, just add a comment to [this bug]("https://bugs.launchpad.net/proposed-tracking/+bug/235555") for i386, or [this bug]("https://bugs.launchpad.net/proposed-tracking/+bug/235558") for amd64. This is a makeshift setup for providing a metric to the QA and release teams on how many people are running *hardy-proposed*. It's temporary and we'll have a more elegant one in the near future.
 

[*] To help us track the hardware test coverage, please upload your hardware profile for the system you will run *hardy-proposed* on using hwtest-gtk ("System -> Administration -> Hardware Testing"). You can see your submitted information at [https://launchpad.net/~your-launchpad-username/+hwdb-submissions](https://launchpad.net/~your-launchpad-username/+hwdb-submissions).


[*] Visit [http://people.ubuntu.com/~sbeattie/sru_todo.html](http://people.ubuntu.com/~sbeattie/sru_todo.html) to see a list of pending stable release updates that still need verification. Click the link for the bug whose fix you're interested in testing, and follow the test case instructions provided by the developer(s) in the bug comments. You can also see a list of all bugs targeted for Ubuntu 8.04.1 at [the 8.04.1 milestone page at Launchpad.]("https://launchpad.net/ubuntu/+milestone/ubuntu-8.04.1")
 
[/list]

---

### Post by danbh on 2008-07-01
the link in step 4 is invalid

---

### Post by 23meg on 2008-07-01
That's because you need to replace the "your-launchpad-username" part with your Launchpad username. 

I know it's better to just use [https://launchpad.net/people/+me/+hwdb-submissions](https://launchpad.net/people/+me/+hwdb-submissions), where "+me" redirects to whatever your LP username is, but that was failing at the time I posted the guide due to a problem with LP.

---

### Post by Gina on 2008-07-01
I can't get either link to work - replacing the place-holder with my user name.  I did get the link in step 4 to work from my laptop and put that into Launchpad shortly after this thread was started.  But I've had no joy from either desktop.

---

### Post by MemoryDump on 2008-07-02
make sure you have an active account with launchpad.
I just tried mine and it worked: [https://launchpad.net/~memorydump/+hwdb-submissions](https://launchpad.net/~memorydump/+hwdb-submissions)

---

### Post by Gina on 2008-07-02
Oh yes - I do have an active account and quite often use it.

---

