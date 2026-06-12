---
title: "Impending Ubuntu 8.10 Release - Frequently Asked Questions"
date: 2008-10-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nhandler on 2008-10-30
Barring last minute changes, the final version of Ubuntu 8.10 (codenamed "Intrepid Ibex") is set to be released today (October 30th, Thursday). The information below is meant to address the frequently asked questions and common misunderstandings that recur before every release.

[LIST][*]**I already have a working Intrepid test installation. Do I need to install from scratch, or can I upgrade when the final release is out? Is there any difference between a clean install and an upgrade?**

You **do not** need to download the disk images in order to have the final release. The update manager will alert you of the existence of a new version when the release is out, and once you've performed a distribution upgrade, you'll have an identical set of packages to those on the CD.

However, it can be a good idea to do a clean install if you're affected by certain corner cases where you may not be able to access specific features or fixes without doing a clean install, or if you've extensively modified or partially broken your installation, and/or have installed software not provided by the official Ubuntu repositories without keeping track of the changes made to your system.

You can also [use rsync]("https://help.ubuntu.com/community/RsyncCdImage") to update your already downloaded disk image instead of re-downloading the entire image.

[*]**When exactly will the release be out? What time?**

The [steps]("https://wiki.ubuntu.com/ReleaseProcess") taken in preparing a release are complex, and depend on the work of multiple people and teams, and the state of network connections; it's not possible to state a specific time of day for the release beforehand.

[*]**Is there a chance that the release will be delayed?**

Even though no delay has been announced up to this point, it's entirely possible that some last minute issues can crop up and delay the release. In the case that a significant delay occurs that necessitates pushing the release date ahead, that will be announced in the [ubuntu-devel-announce mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce"). If you aren't subscribed to the list, you can view the latest posts in [the list archive page for the current month]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-October/date.html") with your web browser.

[*]**When should I download the release?**

If you have to actually download the release disk images, please do so **after the release announcement**, which will be sent to the [ubuntu-announce mailing list]("http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce"). If you aren't subscribed to the list, you can watch for the announcement in [the list archive page for the current month]("https://lists.ubuntu.com/archives/ubuntu-announce/2008-October/date.html") with your web browser. You may also want to join the #ubuntu+1 chat channel at the irc.freenode.net server with your IRC client, where the you'll get notified of the release on the minute.

[*]**I saw a link posted on a blog post / forum thread to a page under the cdimage.ubuntu.com domain where the release ISO seems to be available, and/or a wiki page with links, and/or a page on the Ubuntu website that announces the release. Does that mean that 8.10 has been released?**

Not necessarily. The disk images may be visible on the website a certain time before release; that doesn't mean they're up to date and safe to download. Certain pages on the Ubuntu website can be put online a while before release for testing, passing on to the news media or other purposes; that doesn't necessarily mean the release is out.

The "green light" you should be waiting for is the release announcement (see the above question).

[*]**What happens if I download before the release is actually announced?**

You'll most likely end up with a broken disk image, and since you'll be taking up bandwidth that should be used for synchronizing the disk images across the mirrors worldwide, you'll be delaying the release.

[*]**How can I help [test]("https://wiki.ubuntu.com/Testing") the final disk images?**

Read [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures) , [pick a test case]("https://wiki.ubuntu.com/Testing/Cases"), perform the test and report the results at [the testing tracker]("http://iso.qa.ubuntu.com/"). It's a good idea to join the #ubuntu-testing channel at irc.freenode.net where you can get coordinated with other testers.

[/LIST]

NOTE: This post is nearly 100% identical to the [post]("http://ubuntuforums.org/showpost.php?p=4768946&postcount=1") made by [23meg]("http://ubuntuforums.org/member.php?u=11472") prior to the Hardy Heron release.

---

