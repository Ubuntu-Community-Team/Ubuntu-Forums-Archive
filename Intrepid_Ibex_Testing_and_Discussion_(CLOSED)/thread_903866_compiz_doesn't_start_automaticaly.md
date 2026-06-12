---
title: "compiz doesn't start automaticaly"
date: 2008-08-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hexion on 2008-08-28
In my box with hardy it works normally, but in the intrepid box compiz doesn't start with the session.

Launching compiz from a terminal works ok. No errors.
/home is shared but I use a specific account for testing purposes and the same configuration will work in hardy. I also tried dumping $HOME/.config/compiz with same results.

Any other out there with this?

---

### Post by lovinglinux on 2008-08-28
Install [fusion-icon ]("apt:fusion-icon") then open System > Preferences > Session and in the "Startup Programs" tab create a new entry with the name "Compiz Fusion-icon" and command "fusion-icon".

I guess this should do the trick.

Edit: oops, I thought this was a post from a newbie like me talking about Hardy....

---

### Post by ronacc on 2008-08-28
its been that way from the begining of intrepid and its not just compiz , even it you install fusionicon that won,t start with the session and also other apps that have nothing to do with compiz . It is already reported as bug#249265

---

### Post by lovinglinux on 2008-08-28
> **ronacc said:**
> its been that way from the begining of intrepid and its not just compiz , even it you install fusionicon that won,t start with the session and also other apps that have nothing to do with compiz . It is already reported as bug#249265

Sorry, as I included in the Edit portion of my previous post, I didn't realized this was a Development & Programming discussion. I reached this thread from general Ubuntu rss feed, which I'm using for the first time today. My reader, or the Ubuntu feed itself, do not specify which forum the message was posted. 

I will pay more attention on this from now on.

---

### Post by hexion on 2008-08-28
> **ronacc said:**
> its been that way from the begining of intrepid and its not just compiz , even it you install fusionicon that won,t start with the session and also other apps that have nothing to do with compiz . It is already reported as bug#249265

Cool, bug reported :)
Apart from that, I tried adding a new line in the session manager in gnome but it doesn't allow creating a new line for compiz. Is it reported as well?

lovinglinux, no problem ;)

---

### Post by ronacc on 2008-08-28
I don't know if that has been reported , go ahead and file on it and it should bring up anything that seems like a dupe so you can either add comments to an exisitng report or file a new one , 
@lovinglinux stick around and join the fun:)

---

### Post by lonniehenry on 2008-08-28
I have a strange problem. If i add a to the session preferences menu,  I get a message "The startup command can not be empty" even though I have typed in the correct startup command.  Any ideas?

---

### Post by ronacc on 2008-08-28
I suspect they still have some problems with policy kit and console kit , they did patch them awhile back to cure a couple of bugs but I don't think they got them all  , check launchpad and see if a bug has been filed on it if not file one.

---

### Post by lonniehenry on 2008-08-28
In looking at policykit on Launchpad, apparently sessions shouldn't be covered by policykit.  I would think that it should be. So I still don't know what is going on.  Thanks for your reply.

---

### Post by ronacc on 2008-08-28
you can go ahead and file the bug and leave the package as "unknown" and they will sort it out .

---

