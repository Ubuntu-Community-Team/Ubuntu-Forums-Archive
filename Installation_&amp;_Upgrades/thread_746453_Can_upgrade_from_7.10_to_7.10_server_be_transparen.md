---
title: "Can upgrade from 7.10 to 7.10 server be transparent?"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by barney_xuf on 2008-04-05
After a couple hundred of hours of configuration & tailoring, I've discovered that I should have installed the server version of 7.10 - and I really don't want to lose the time I've invested to date.  

On the other hand, I don't want to spend more time tailoring if I need to install the server version.

So the question would be, I guess, whether there is a way to save [certain] current installations/configs, install 7.10 server, then restore those configs?

This same question will arise when I upgrade from 7.10 to 8.x, so I'd like to get a resolution, one way or the other, now.  If a graceful upgrade can be made, which I'm beginning to doubt, then I have relatively few problems.  However, if the upgrade is wipe-and-replace, then I need to start logging installs/configs for later reference.
(For example, Virtual Box with a tailored instance of WinXP - I'd hate to lose that config - so I'd naturally copy the VMI, VMD, *et. al., *files to a different drive, then copy them back - with about a 50-50 chance that would work, from what I've read.)

Anent which, is there some way to list *every *app currently installed?  Command line or GUI, although GUI would be better, methinks - I keep running out of room in the command line buffer <chortle />.

---

### Post by kellemes on 2008-04-05
I wonder why you need the server edition..
If it's a server you need, you can just as well set it up from your current (desktop) install.
Since it's a server you may wish to strip a little, but this surely is a smaller task then reinstalling from scratch.
I ask this because it seems odd to me you're willing to keep your Virtual XP, a server preferable shouldn't be more than a server.

---

### Post by barney_xuf on 2008-04-05
> **kellemes said:**
> I wonder why you need the server edition..
If it's a server you need, you can just as well set it up from your current (desktop) install.
Since it's a server you may wish to strip a little, but this surely is a smaller task then reinstalling from scratch.
I ask this because it seems odd to me you're willing to keep your Virtual XP, a server preferable shouldn't be more than a server.

OK ... not unexpected ... so I'll explain the need.  This **will** be long.

My income is derived from developing web-based, [primarily] database-driven applications.  The pittance I make from such venues as AdSense, Chitika, *et. al., *can't keep me in beer and cigarettes, much less pay the rent.

My primary tools, at this point, are Apache, MySQL & PHP. (Ruby/Rails is in process.)

Whether WAMP or LAMP, I need server-based tools.

So far th;is year I've had three major crashes on a Win XP Pro (Media Edition) machine.  The first was due to an errant install of one or more security updates.  The 2nd was probably the same, although it may have been due to software that I'd installed - the time frame was too close to say one way or the other.  I've no idea what caused the 3rd, but that one required a *hard *reinstall, *i.e., *wipe the drive and install from scratch.

Last time I played with Linux was about 1997, a Red Hat version.  Had no significant problem with the command line area, but the X widow GUI was somewhat lacking.

A person whose opinion I respect suggested Ubuntu as an alternative for the base OS, then WINE and Virtual Box to support the XP necessities.

Since there are several Ubuntu flavours, I installed XUbuntu, KUbuntu, and Ubuntu (Gnome).

I loved the Xfce (?) interface, but there was too much I could not find out how to do.  I like the KDE interface - it seems more oriented to development, at least to me - but it crashed twice (reinstall required) during the post-install update.  The Gnome interface has given me the least trouble and has provided the most access to elements I needed to be able to see/configure.

Until it came time for AMP.

Installed Apache, but couldn't do much with it except as root.
Same with PHP.
MySQL was a disaster - could not even set the password.  And I was following instructions every step of the way on each one.

Ubuntu won't let me log in as root.  Yes I'm aware of the many arguments against it, but I'm also aware of some arguments for it that seem to be ignored by those against.

That aside, I simply cannot do my job with Ubuntu as it is currently configured.

Discussing this with a friend, the one who started me on the Ubuntu path to begin with, he mentioned that I should have installed the server version.

I would go over this with him, as he is knowledgeable in this realm, but he and his mate left on a *world cruise *a couple of weeks ago, and won't be back 'til some time in late July or early August.  No laptop, no email, no cell phone (his wouldn't have worked outside the US, anyway).

That's the rationale for installing the server version.  If I had a spare machine, I'd put it there and thus address it properly.  I don't have a machine strong enough to do the job.  So it goes on my work machine, which will end up doing double duty.

Now, as to the virtual XP.

There are too many Windows apps that simply have not been replicated in the Linux environment.  Many of these cannot run well under WINE.

In addition, Internet Explorer does not deal consistently with CSS, so I need at least v5.x, v6.x & v7.x to test my interfaces.  And I've found that Firefox does not perform the same under Linux as under Windows.

In another venue, I simply have not been able to view/hear multimedia in any reliable fashion.  Oh, I can play a CD/DVD as far as audio is concerned, but video just ain't happenin' whether Web-based or standalone.

So ... that's why I asked the server install question.  I was hoping for a quick, "Yes, this is how," or, "Nope, can't be done."



Which brings me to another point, one that will probably alienate most of you who read it.

Some of you may be familiar with Tek-Tips, a support forum for just about anything having to do with programming and coding.

Quite a few years ago, I was a member of that forum group.  In fact, I was credited, by the then owner and founder, with [probably] saving it.

My expertise at that time was Visual Basic (VB).  I answered a lot of questions, resolved a lot of problems, in the VB forae.

I answered the questions.

When I thought I knew a better way to accomplish *what I thought the person asking the question wanted to accomplish, *I'd suggest alternatives.

After I answered the question.

See, most of the time, the questioners didn't want my opinion, they wanted resolution to a problem that they had.  So I gave 'em that answer. Then, if I felt it was warranted, I gave 'em alternatives - my opinion.

I left Tek-Tips when it became *elitist, i.e., *the responders to posts came across as though the person asking the question was stupid for asking it.

I've seen some of that here, in the Ubuntu forae.

~~~Sidebar ~~~
I do not point this at you, *kellemes, *but felt I needed to clear the air insofar as my questions - and my attitudes - are concerned.  You asked an honest question, flavored by an opinion seemingly based upon your concept of my question and offering a better approach.  Indeed, yours may **be** the better approach.  But, to date, it hasn't worked for me, thus the question about *upgrading  *(or downgrading?) to the server version.
~~~End sidebar~~~

If I ask a question, it's because I feel the need for an answer.

If I ask for an opinion, all bets are off, and I'll not resent any opinion voiced.

But if I ask for help, it's because I need assistance in performing some action that I do not yet have an acceptable way of performing.  And it's an action I need to perform *soon *if not **now**.

If this made sense to any one of you, I'm glad.  If it alienated any one of you I'm sorry.

 Flame on.

Make a good day ...
                         ... barn

---

### Post by kellemes on 2008-04-06
You need to understand the basics of managing a GNU/Linux system, the use of privileges, the risks you take when dealing as root. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
As a server administrator you need to be interested in understanding all aspects of setting up and maintaining a server. You're going to have to deal with the same issues when going server-edition.
If you're not able to setup Apache or MySQL on Ubuntu Desktop you're going to have an impossible task ahead..
If you need more then LAMP (seems to be), you can go from the Desktop edition.
Creating server from desktop is stripping all crap (including some virtualbox-install) and install whatever stack you need.

---

### Post by kellemes on 2008-04-06
What you need is a developers-platform instead of a server-platform, for this Ubuntu is fine, although there are others. Why not try Fedora, openSuSe, centOS or one of the 350+ others.. I'm a db-developer also and making use of Debian, although mainly Windows.
You can always setup your system such you can install another distro (or the server-edition) besides your current Ubuntu install, so you won't lose your configuration. This way you can investigate if it's providing what you need.

If you need any help with whatever choice you make I'm perfectly willing to help.

---

