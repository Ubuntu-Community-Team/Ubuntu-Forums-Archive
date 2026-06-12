---
title: "Installing VMWare Player"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by Tony D'Ambrosio on 2007-06-25
Setting the scene: I am good with computers (mainframe and PC's, both).  Used to be an assembly language programmer (applications), but those days are long gone.  Very recently, as the result of too much contact with my techie son, getting into Linux, specifically Ubuntu.

Installed full software update the other day ...took about 7 hours (I'm stuck with dial-up, here in our rather rural area), but worked fine. I think there were 78 packages in all.

I've tried 2 different sets of directions (found via Internet searches) to accomplish the captioned task.  What happens is when I try (using Terminal) to issue various commands it quickly becomes clear that things are not working.  The common denominator seems to be related to this error message "Could not resolve 'archive.ubuntu.com'.  I don't know what archive.ubuntu.com is, let alone why I am not able to resolve it, so I'm sort of stuck.

I am logging in at the root level (with the # at the end of the prompt), so I imagine I've full authority.

Any suggestions or references will be gratefully received.

Finally, since I've never used this Forum before, I'm not clear on how responses get back to me, whether via posts or emails.  Just in case, I'm at: [email]tonythedamb@aol.com[/email]

Tony D'Ambrosio

---

### Post by Tony D'Ambrosio on 2007-06-25
I was mixed up.  I'm not issuing commands using Terminal ... I'm using TTY1   Tried Terminal and it informed me I couldn't get there from here.

Tony

---

### Post by BatPenguin on 2007-06-26
Hi there,

And welcome to the Ubuntu forums! :D Happened to see your post here, looking up vmware installation instructions myself. I was under the impression that you just download the Vmware Player from their web site, register and go from there...but like I said, haven't done that yet, so just guessing. That's what I was going to do once I get done with this post.

I'm not a very experienced user myself (a few years of linux, less than a year of Ubuntu) so my apologies if these suggestions are too simple or something, you sound like you've been around the scene longer...but to me your problem sounds like either:

1) problem with the repositories. Go see whether all the repositories (multiverse, whatever) are enabled in Synaptic: System -> Adminstration -> Synaptic Package Manager. It sounds like there might be a problem with connecting to one of them.

OR

2) you're issuing commands that need root access without the root permissions, meaning without typing "sudo" in front of the command. Unlike some other linuxes (at least the ones I've used: Fedora, SuSE and RedHat), Ubuntu doesn't really use the root user but rather, the "sudo" ("super user do") command that gives a user (who has been specified to be able to use such permissions) a temporary right to issue commands with root permissions. So: if you're trying to issue the command "cat /etc/messages/boot.log" as root, you'd type "sudo cat /etc/messages/boot.log" etc...that sorta thing. It'll ask for your USER password. Just type that, and you're authenticated. The default user is created with possibility for using sudo.

Hope this helps :)

---

### Post by dabl on 2007-06-26
VMWare Player ver. 2 is available by downloading from their web site.  There is an earlier version 1.something in the repositories.  Either one seems to run my Win XP virtual OS, so it may not matter which you go with.

---

