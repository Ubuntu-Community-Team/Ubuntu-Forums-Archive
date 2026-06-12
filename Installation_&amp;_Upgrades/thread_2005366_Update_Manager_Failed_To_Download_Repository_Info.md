---
title: "Update Manager: Failed To Download Repository Info"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by danieldiazdon on 2012-06-17
My Update Manager keeps telling me that it hasnt been updated in 8 days. When I try to update I get an error saying "Failed to Download Repository Info." Here are the error codes in the Update Manager. 
[IMG]http://i.imgur.com/RV1L4.png[/IMG]

From there I ran "update" in the terminal to get another picture of what was failing, and this is what came up. Everything worked until the last few links.

[IMG]http://i.imgur.com/lD7BU.png[/IMG]

The only thing that this issue may be tied with is that I recently updated to Java 7 and then I uninstalled Java 6. However, I realized that I still needed it so I reinstalled Java 6 and am now running both. How do I fix this? Am I to delete those repositories? If so, then how. Thanks a ton :)

---

### Post by drs305 on 2012-06-17
danieldiazdon,

Welcome to the Ubuntu Forums.  :-)

I checked the repository and at present there is only a "natty" archive. Either change your sources.list file or the file in /etc/apt/sources.list.d for this repository to 'natty' or, if you used 'precise' before, wait to see if it comes back online.

If you don't know how to do this just ask and someone will be glad to provide the details.

---

### Post by danieldiazdon on 2012-06-17
> I checked the repository and at present there is only a "natty" archive. Either change your sources.list file or the file in /etc/apt/sources.list.d for this repository to 'natty' Okay, that makes sense. I just have no clue where to begin or how to do it. Can someone please explain to me how to fix my problem? Thanks guys :D

> if you used 'precise' before, wait to see if it comes back online.Just out of curiosity, what did you mean by this? That the repository is down or that one hasnt been created yet and will be?

---

### Post by drs305 on 2012-06-17
Sometimes a repository is removed from access while the maintainer updates it. Sometimes a specific release doesn't exist. In this case, I don't know if the creator has one for 'precise' or not. I'm guessing not, since there is no repository for 'oneiric' either.

Generally you should be using a repository for the Ubuntu release you are using. When using a non-official repository, you are relying on the maintainer to make sure things work. If you use a repository designed for an earlier release of Ubuntu, you are increasing the risk that it won't work with your current version. It may, but it very well may not.

So your course of action is 1) not using thoroughly tested Ubuntu repositoreis, and 2) using a repository that may not be designed for your release. 

This doesn't mean the repository packages from launchpad ppa's are bad - not everybody can just add a repository in launchpad.

My point is that if you have used this repository before, with precise, there is a good chance the maintainer has just pulled it down for maintenance.

If you haven't used this repository before, just realize that changing to the 'natty' repository is not normally recommended. Ubuntu and Linux in general is about choice, so it's your decision. As you are new to the UF I don't know how much experience you have had with repositories, so I wanted you to have a clearer understanding of what is happening.

Now, as to changing the repository, if you still want to, you can do it via a text editor or via command line. Since I don't have the time for a fuller explanation, here is the command line version:
```
 sudo sed -i 's/precise/natty/g' /etc/apt/sources.list.d/dlecan-dlecan-precise.list
sudo apt-get update
```
This command will work if you added the repository with the "add-apt-repository" command but may not if you added it in a different manner.
Update: the command did not work for the OP as the file was named "dlecan" rather than "dlecan-dlecan".

This will change "precise" to "natty" so you can pull up the natty packages. To change it back to precise, reverse the words. Note that when you run the package, after entering your password (which you won't see) there will be no output in the terminal. In Linux, if there is an error, a message is normally created. No message means no error!

Ask if I've confused you further.

---

### Post by danieldiazdon on 2012-06-17
Perfect explanation! However, I believe that the repository for "precise" doesnt exist cause I was messing with the JDK installation through Software Center about 8 days ago. And thats how long Update Manager has said that it hasnt updated. Unfortunately for me though, your solution did not work... :/ This is the error:
[IMG]http://i47.tinypic.com/zml05x.png[/IMG]

> This command will work if you added the repository with the  "add-apt-repository" command but may not if you added it in a different  manner.In regards to this, I didnt do anything specific to add the repository. Im pretty sure it was done automatically when I installed Java 6 or 7 through the Ubuntu Software Center. Still, I am unsure of what to do from here. Any other commands or options? Thanks :D

---

### Post by drs305 on 2012-06-17
> **danieldiazdon said:**
> Perfect explanation! However, I believe that the repository for "precise" doesnt exist cause I was messing with the JDK installation through Software Center about 8 days ago. And thats how long Update Manager has said that it hasnt updated. Unfortunately for me though, your solution did not work... :/ This is the error:
[IMG]http://i47.tinypic.com/zml05x.png[/IMG]

In regards to this, I didnt do anything specific to add the repository. Im pretty sure it was done automatically when I installed Java 6 or 7 through the Ubuntu Software Center. Still, I am unsure of what to do from here. Any other commands or options? Thanks :D

Sure. When added using the add-apt-repository command it should have created the file, and in the format, so the command I posted would work. But there are other ways to add the repository so we can look at what you have.

Open the normal repository file for editing:
```
gksu gedit /etc/apt/sources.list
```
Look for the *dlecan* lines and change 'precise' to 'natty'.

If there is no listing in /etc/apt/sources.list, with that file still open, try opening a new file and click on the 'sources.list.d' folder and see if there is a 'dlecan' file in that folder.

Another way is to open the Software Sources. You can do this with the command "sudo software-properties-gtk" or via Ubuntu Software Center: Edit>Software Sources. In either case, look in the 'Other' tab, find the 'dlecan' listings (there will probably be 2), highlight > Edit, and change 'precise' to 'natty'.

One thing you will quickly learn about Linux - there are usually a lot of ways of accomplishing the same goal.

---

### Post by danieldiazdon on 2012-06-17
PERFECT. It is now SOLVED. The *dlecan* was not found in the "sources.list". Instead, I went ahead, opened a new file, went to "/etc/apt/" and found the "sources.list.d" folder. Inside of this there was the *dlecan*. I went into the highlighted one.

[IMG]http://i46.tinypic.com/6qbc5l.png[/IMG]

Once, I opened it, I saw the following and changed "precise" to "natty"

[IMG]http://i49.tinypic.com/2iicuut.png[/IMG]

From there, I saved everything, and closed the files. I then ran "Update Manager" and it updated flawlessly. 

[IMG]http://i48.tinypic.com/167ktc9.png[/IMG]

Just wanted to say THANKS A TON! Your explanations were perfect and your instructions couldnt have been clearer. I included pictures of everything so that if anybody has a similar problem, they can go right through the steps you provided and solve their problem. And, to respond to one of your comments, the more that I use Ubuntu, the more I realize that there are multiple options PER scenario. Once again thanks :D

---

