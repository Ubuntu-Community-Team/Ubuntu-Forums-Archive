---
title: "Should vim and Emacs be part of the basic distro?"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-03-03
Regarding to post [http://ubuntuforums.org/showthread.php?t=1085342](http://ubuntuforums.org/showthread.php?t=1085342) I think it would be a good idea to open a poll for this issue.

My point of view is that these editors are part of the LINUX legacy and an important addition used in many instructional documents. Therefore they are even for mainstream users an important tool that can not be sacrificed for a bit more space in the distro.

---

### Post by MacUntu on 2009-03-03
I do like vim but be honest: no mainstream user will ever use either of those editors. I'm okay with not having them on CD because I know how to install applications.

---

### Post by BwackNinja on 2009-03-03
I'd say they are pretty much useless to anyone new, unless they put out the effort to learn how to use them. A new user is liable to be completely oblivious to their existance and not even know how to edit text in vim or quit vim beyond closing the terminal ( and that doesn't exactly save :D ).

Being able to install them easily is one thing, but problems would arise if you need to get something done from a livecd. I wouldn't think that you would really ever need any extremely powerful text editor from a livecd though.

---

### Post by philinux on 2009-03-03
Most newbies and ol'timers are happy with gedit. If anyone needs vim or emcs they already know how to install them.

---

### Post by Simian Man on 2009-03-03
Vim must be kept because it is the universal Unix text editor.  It may as well be part of the Posix standard from my perspective.  Besides it is extremely small and won't get in a users way if he doesn't know it is there.  Most users don't know or care about things like traceroute yet they are included.

Emacs I don't care about.  Is it even included now?

---

### Post by meborc on 2009-03-03
its a tie :D

i guess you need at least a few thousand answers before drawing any conclusions

---

### Post by taavikko on 2009-03-03
> **philinux said:**
> Most newbies and ol'timers are happy with gedit. If anyone needs vim or emcs they already know how to install them.

Yep,

Neither one should be on the liveCD (size does actually matter)
But both of them should be made installable easily
"# apt-get install vim"

But for me, I'll use "cat"/"sed"/"echo" for my editing purposes ;)
Cause I  just don't gedit...

---

### Post by issih on 2009-03-03
There is no need to duplicate such basic functionality as a text editor.. one will do. To that end unless we are going to become a programmer's distro, a gui one is the only logical choice.

I have to say that I actually doubt that either of them take up enough space for it to be a serious concern, even on something as tight on space as a live cd, but it there is a need for more space, and it will actually free an appreciable amount, then chuck them out.

Anybody who really needs these tools for their productivity will be more than capable of installing them anyway.

---

### Post by Simian Man on 2009-03-03
I use the LiveCD to rescue existing systems.  In that scenario I cannot just install vim from the repositories, but need it to work efficiently.  Also what if you are using Ubuntu but don't have root access.  vim is essential and tiny.

---

### Post by gnomeuser on 2009-03-03
I would like to see vim continue to be available, emacs is frightfully big and appeals to very special usecases. We should have a good text editor in the default install though, it is a nice last line of defense for bringing back X e.g. or applying small configuration changes.

---

### Post by Simian Man on 2009-03-03
> **gnomeuser said:**
> it is a nice last line of defense for bringing back X e.g. or applying small configuration changes.

Good point!  How useful is gedit going to be when your X server crashes?

---

### Post by philinux on 2009-03-03
In this situation I'd use nano.

---

### Post by Nullack on 2009-03-03
sudo nano -w has gotten me out of a bunch of alpha problems over time

And really, how hard is apt-get install whatever

---

### Post by autocrosser on 2009-03-03
I have used nano for years & it's footprint is rather small...So, why should a LiveCD come with Vim, Emacs & Nano? My vote is that one will do & the smallest footprint wins.....If one is recovering a system there are several purpose-built CDs just for that use...or one could make one including your favorite apps.....I would say in 90% of the cases, the LiveCD is being used to install a system & that is where we really need to shine.

---

### Post by nyarnon on 2009-03-03
> **autocrosser said:**
> I would say in 90% of the cases, the LiveCD is being used to install a system & that is where we really need to shine.

I would challenge that. The livecd is at least if not more used in system repair instances. And guess what most documents covering linux system repair favour as an editor?

---

### Post by MacUntu on 2009-03-03
> **nyarnon said:**
> I would challenge that.

You would challange something based on nothing with something based on nothing? Time for popcorn! :popcorn:

---

### Post by zacktu on 2009-03-03
I prefer vi instead of vim -- just don't know of anything I can't do with vi.  Will jaunty also remove vi?  ex?  ed?  (They're all in intrepid.)  I would use any of those before using gedit.  It looks too much like notepad.  

I didn't realize that Ubuntu was trying to appeal only to people who are afraid to use the command line.

Keep vim and emacs.

---

### Post by ronacc on 2009-03-03
The sad fact is that as long as Ubuntu is to remain a single cd install choices will have to be made and duplication of function is wasteful . I doubt that the "normal" desktop user will have any real need for vim , emacs or even nano .If you do have a need they can be installed and there are tools to build your own live cd .Many would prefer a different player than gstreamer but we don't include 5 of them on the cd .They should be in the repos .

---

### Post by MacUntu on 2009-03-03
There's still a Live-DVD: [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

---

### Post by Nullack on 2009-03-03
I agree with nyarnon - when things are really toasted its time for system rescue by booting an ubuntu cd and working on fixing from there.

---

### Post by gnomeuser on 2009-03-03
> **Nullack said:**
> sudo nano -w has gotten me out of a bunch of alpha problems over time

And really, how hard is apt-get install whatever

When the file I need to edit to get my system back is the network configuration or /etc/apt/sources.list.. very.

Not that nano is a horrible editor but vim is widely used, people know it. It is easier to find good guides for using it and for experienced users to give help if they know that the tools they are used to is there. For the scenerios we would want a text editor, we would often also be talking about users with a certain level of experience, that means vim is a far better fit.

---

### Post by gnomeuser on 2009-03-03
> **ronacc said:**
> The sad fact is that as long as Ubuntu is to remain a single cd install choices will have to be made and duplication of function is wasteful . I doubt that the "normal" desktop user will have any real need for vim , emacs or even nano .If you do have a need they can be installed and there are tools to build your own live cd .Many would prefer a different player than gstreamer but we don't include 5 of them on the cd .They should be in the repos .

apple and oranges my good man. gstreamer isn't a player, a multimedia framework. Besides the CD actually does ship two players, totem and rhythmbox.

One argument for not shipping a text editor would be that the CD can act as a rescue disk (look at how Fedora handles this - quite elegant and very handy, all distros really should have this). That however would not work for most netbooks as they have no CD drive, nor for the many people who borrow a CD to install or have a friend install it. If there is no cd and we can't redownload it, then we are screwed.

---

### Post by klange on 2009-03-03
Why would we add an editor with a brick-wall learning curve or an editor that includes everything *and* the kitchen sink?

Ubuntu is targeted at a shallow learning curve.
Ubuntu ships with Nano.
Nano is an editor with a shallow learning curve.

Stop trying to make a problem where one doesn't exist.

---

### Post by nyarnon on 2009-03-03
> **WindowsSucks said:**
> Why would we add an editor

Why don't you read the thread? There are a lot of arguments for it, not always to be understood by the 'targeted population' but never the less very legit. 

In fact the only argument against it till now is an reiteration of the same boring argument. We don't understand it so we don't want it.

---

### Post by issih on 2009-03-03
I am convinced by the argument that there should be at least 1 console based text editor for system rescue when X has gone down the plughole.

As I said last time, anything with a tiny footprint in terms of size on disk might as well stay..anything big should be for the high jump where it replicates functionality, at least if there is a size issue, and as long as we use live cds there is likely to be a size issue.

Theres no reason we couldn't fork the cds so there is one intended for install and one for rescue if things get really tight on space.

That way the rescue cd could have as many console tools as you want and sacrifice something like open office..that ought to make some room :)

---

### Post by issih on 2009-03-03
Just to add some numbers to this thread, and bearing in mind that emacs can almost certainly be pared down to something a lot smaller, probably approaching vim's size if we want to keep it around as just a basic text editor and not have all the extras in there too:

Compressed size quoted below each link is a bzipped download image and therefore hopefully comparable to the size on disk in a compressed live cd environment.


nano 1.4MB compressed, 8.3MB deflated
[http://www.linuxfromscratch.org/blfs/view/stable/postlfs/nano.html](http://www.linuxfromscratch.org/blfs/view/stable/postlfs/nano.html)

Vim 6.6MB compressed, 75MB deflated
[http://www.linuxfromscratch.org/blfs/view/stable/postlfs/vim.html](http://www.linuxfromscratch.org/blfs/view/stable/postlfs/vim.html)

Emacs 36.4 MB compressed, 260MB deflated
[http://www.linuxfromscratch.org/blfs/view/stable/postlfs/emacs.html](http://www.linuxfromscratch.org/blfs/view/stable/postlfs/emacs.html)

As compressed sizes then, including vim and emacs in full over and above nano will eat about 43Mb or about 5.7% of the cd's space


If instead we assume we include a pared back emacs, it should apparently be only slightly larger than vim ([http://essays.hexapodia.net/emacs-large/](http://essays.hexapodia.net/emacs-large/))

Therefore assuming a compressed size for emacs of 7Mb we have a total size requirement of 13.6MB to include both which is about 1.8% of the total disk space.

To my mind the former is unacceptable, the later probably is ok.

Just thought some actual data would be good..

---

### Post by MacUntu on 2009-03-03
Hm... vim 6860kB vs. vim-tiny 536kB vs. nano 299kB (according to Synaptic).

---

### Post by issih on 2009-03-03
Hmmn I suspect my values are source code packages. I'd trust synaptic values more at any rate, although the size of any dependancies must be taken into account. Sadly I'm away from my ubuntu box at the moment hence the google based solution.

once you get down to those sizes, and applying a guesstimate factor of 6 for compression, I'm back to thinking that they are small enough to be a non issue in most scenarios.

edit..are those sizes from synaptic download size or disk footprint though?

---

### Post by MacUntu on 2009-03-03
Downloaded (dependencies included). Installed (dependencies included):

vim: 27,3MB
vim-tiny: 1290kB
nano: 1769kB

---

### Post by benj1 on 2009-03-03
i understand the point that you don't realy need 4 editors on a distro and its easy enough to install your preferred editor anyway.
But ubuntu will be alot of peoples introduction to Linux, so i do think that we need to keep these things that make Linux different to what they used before. People are more likely to discover these things if they are installed by default, rather than having to go out of their way to download them.

Also the logical conclusion of having a distro with a 'shallow' learning curve would, i suspect be somthing very close to Windows.

---

### Post by MacUntu on 2009-03-03
It's not about keeping it simple, it's about keeping it small so it fits on a CD.

Anyways, is this even official?

---

### Post by simtaalo on 2009-03-03
> **benj1 said:**
> 
Also the logical conclusion of having a distro with a 'shallow' learning curve would, i suspect be somthing very close to Windows.

rubbish

vim+emacs both have a horrible learning curve. i've never used nano before and i just fired it up and i could do stuff without any need for a guide/help/tutorial, it was just simple and easy.

i've tried to use both vim+emacs, both are horrible for anybody but very experienced users.

i don't see what problem anyone would have with nano.

---

### Post by benj1 on 2009-03-03
True
but for the size they take up compared to other apps, if space is the issue getting rid of something that uses kb's isn,t realy going to help, how much space to all the case studies and nelson madela videos you get when you first install take up?

---

### Post by simtaalo on 2009-03-03
> **benj1 said:**
> how much space to all the case studies and nelson madela videos you get when you first install take up?

?

---

### Post by klange on 2009-03-03
> **simtaalo said:**
> ?

/usr/share/example-content

10.6MB on my old, pre-installed 8.04.1 on my Mini.

---

### Post by simtaalo on 2009-03-03
9.8MB here, didn't know that was there. 

seems pointless, seems the kind of content that should be there to download but not on a livecd where space is crucial.

---

### Post by Triggerhapp on 2009-03-03
If im stuck on a command line, without my wireless card working... (btw I generally cant reach ethernet) I would really wish I had a GOOD text editor, I've found nano is too simple for my own use.

---

### Post by simtaalo on 2009-03-03
> **Triggerhapp said:**
> If im stuck on a command line, without my wireless card working... (btw I generally cant reach ethernet) I would really wish I had a GOOD text editor, I've found nano is too simple for my own use.

it might be a little simple, but it wouldn't stop you from doing what you needed to do, it might just take a minute more.

if you didn't have nano, and had vim/emacs you would be actively stopping people from being able to do what they needed if they weren't experienced enough to use those editors.

i think nano is a good middle-ground.

---

### Post by Triggerhapp on 2009-03-03
Im not saying nano's bad for other people, but from my last use of it, regular expression replace wasnt a feature... But i may have just not found that feature...

Also, Looking at the sizes of Vim-tiny and nano, I dont see justification of the "not enough space on CD's" arguement. Speaking of which im currently creating my own live disc because I can.

---

### Post by C0d3Runr on 2009-03-04
Neither should.  Save the space for more important things.  As it is, the vim included in the base install is "vim-tiny", which is nearly useless to non-vim users (who can just use pico) and vim users (who want a *full* vim) alike.  As it is, I believe that the vim in the base install will have it's "vim" alternative removed, and will only provide a "vi" alternative - which is the way things should be.  A base install must have a vi, but it definitely doesn't need vim or emacs.

---

### Post by tgoose on 2009-03-04
From my point of view there's definitely no need to keep emacs in there.  I was under the impression that basically every distro had nano and vi and I don't see why a basic install should need any more.  Anyone who wants to use emacs (like me) can install it afterwards.

emacs itself isn't that useful to me without extra packages (auctex, gnuplot-mode, emacs-goodies-el, octave3.0-emacsen and so on) so whether or not the main emacs package is included I have to install extra packages to actually use it.  I just don't see the advantage of putting it on there.

---

