---
title: "Installing programs from deb files on Ubuntu 8.10/9.04"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nightstrike2009 on 2009-03-12
I thought I'd Index all my threads for those of use that have access to a Windows PC that has the internet, but own a ubuntu PC that doesn't themselves.:D
[B][U]
NVIDIA 3D Driver Installation for 8.10 & 9.04 (Compiz for 8.10 only as yet)[/U][/B]
[http://ubuntuforums.org/showthread.php?t=1092373&highlight=nightstrike2009]("http://ubuntuforums.org/showthread.php?t=1092373&highlight=nightstrike2009")

I have no issues with nvidia driver now

**_3D Gaming on Ubuntu 9.04 (Alpha 5)_**
[http://ubuntuforums.org/showthread.php?t=1094180&highlight=nightstrike2009]("http://ubuntuforums.org/showthread.php?t=1094180&highlight=nightstrike2009")

Sound and Credits don't work on supertux kart rest seems ok

**_Installing Songbird & Handbrake on Ubuntu 9.04 (Alpha 5)_**
[http://ubuntuforums.org/showthread.php?t=1094184]("http://ubuntuforums.org/showthread.php?t=1094184")

Handbrake prob doesn't work fully due to lack of codecs

---

### Post by ivanvajar on 2009-03-12
??? :-) What is your question????

---

### Post by Paqman on 2009-03-12
I'd just like to point out that there's no way anybody coming to the Absolute Beginners section for answers should be running Jaunty. It's still in Alpha, and not at all recommended for people new to Ubuntu.

Just to prove a point, i'm not new to Ubuntu, and I currently have a b0rked Jaunty on my spare partition. Don't do it kids! :D

---

### Post by Nightstrike2009 on 2009-03-12
In reply to ivanvajar I wasn't posting a question my friend, I was trying to provide answers all in one place LOL. 

Do you know whether or not the Ubuntu 9.04 (Final Version - Due 23rd April) will have Python 2.6 as standard or is this just a rumour? If it does I maybe able to get compizconfig working on it without too much grief. ;)

In answer to Pacman, I disagree I am new to ubuntu but have used linux at odd times during its evolution, I am from Ubuntu 8.04 & Ubuntu 8.10 an running 9.04 alpha 5 to learn more about linux before final release version. I have also used Fedora, Opensuse, Linux Mint, Mandriva/Mandrake in the past and am new to Ubuntu. I agree with Pacman that its not for everyone as its still in testing but already I am finding it better and easier than Ubuntu 8.10.  

I'd also like to point out without testers Linux would not be able to evolve as fast has it does, each to our own even if we are newbies, if you want to try it don't let it put you off have a go if it doesn't work for you you can always install 8.10 for free anyhow, least you had a try and learned something. :)

I'd also like to point out some of these solutions are for Ubuntu 8.10 not just Ubuntu 9.04 (Alpha 5) and are clearly marked. :)

---

### Post by nyarnon on 2009-03-12
That's a silly idea, abusing the forum to create a blog or a homepage. There are other places to do that, create a blog link it in your signature if you ensiste doing something like this.

Please consider how this forum would look like if every one would do this? New and current messages wouldn't appear anymore. IMHO this is clear abuse and one of the admins should remove this as soon as possible.

---

### Post by jfernyhough on 2009-03-12
@OP
1) You're creating a post to link to posts you've already created. Why? The forum search will do that for you (find all by author).

2) The individual posts don't really offer anything to the development process. This isn't a place for how-tos, especially when it involves installing a single piece of software straight from the standard repos. Installing obscure speciality software - OK. Installing a dev version from source - OK. Installing TuxRacer? No.

This could be explained if this has been moved from Absolute Beginners, in which case Pacman has already made the point that beginners shouldn't be using a development version, and as such don't need to be told how to install Jaunty's software!

> Do you know whether or not the Ubuntu 9.04 (Final Version - Due 23rd April) will have Python 2.6 as standard or is this just a rumour?Already at version 2.6.> If it does I maybe able to get compizconfig working on it without too much grief.It worked with 2.5, it's been rebuilt with 2.6, works fine.

Actually, I've just realised what you're doing and it's going to lead to nothing but pain. There are package managers for a reason; one of which is to solve dependencies. Synaptic and aptitude will take care of installing everything you need, so downloading individual debs really is a waste of time. As for running Ubuntu on a machine without internet access, yet having a Windows machine that has access? Why? Why not just connect the Ubuntu machine to your network?

Running a development version is hard enough without introducing dependency issues by downloading and installing debs manually. I can't remember if a manually installed version will automatically be upgraded by a newer version from the repo, but if it doesn't then you're going to end up with wrong versions and weird issues. Even if they do, when you try to install from a deb that you downloaded a while ago you'll end up getting errors as it will expect older packages than those installed on your machine.

To sum up:

It's not worth it. :D

---

### Post by Nightstrike2009 on 2009-03-14
I was just trying to help new users get things up an running but you both have a valid point. I would point out this was originally posted in **"Absolute beginners"** originally and moved here.

[I]I am installing debs manually because the windows internet machine i have access to isn't running linux. My Windows/Ubuntu machine is not on net so I have to install everything via deb files from the windows one with the internet. 
[/I]
I understand this is not ideal as would be much easier with internet on ubuntu machine. Sadly this is not an option at present time so I am just using what I have. The Windows (Internet) PC is not owned by me but I am allowed to use it for file downloads, its owner has no interest in Ubuntu, they are not networked either.

Thanks for your helpful advice, I know I maybe making mistakes a first but I intend to learn from them, and advance my knowledge of ubuntu. :)

PS: I intend to upgrade to Ubuntu 9.04 on final release was just trying to get a head start, I already find i need new files with every new release i realise this is part of Ubuntu's evolution and something I must adapt my limited know-how to as it changes and new files are required, as I am willing to do.

UPDATE: Briefly defected to Kubuntu 9.04 Alpha 6, as they are very similar I now have the info I need to get what I wanted working as ubuntu runs same .deb files. Now updated to Ubuntu Alpha 6 and everything is now fine. I find if you can't get the advice you need quickly a bit of DIY is in order even if it involves using .deb files and testing versions. I have learned a lot from the experience, sheep keep making same mistakes, individuals learn and evolve.

> [B]"I'm generally a very pragmatic person: that which works, works." Linus Torvalds

"The Linux philosophy is 'Laugh in the face of danger'. Oops. Wrong One. 'Do it yourself'. Yes, that's it."  Linus Torvalds [/B]

---

