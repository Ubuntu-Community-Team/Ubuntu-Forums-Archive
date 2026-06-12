---
title: "was trying to install medibuntu repository from command line"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-04-07
Hi,

I recently discovered the medibuntu repository and wanted to add the  repository to synaptic. I copied and pasted the code from this:  [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php) web page on medibuntu.org's website.

The attachment shows exactly what the terminal spit out after running  this command (and the command that was run - of course). What I am  wondering about is the last six lines - which seem to indicate that, at a  minumum, getting some key was not successful. I'm not sure how  important this is; but, since I don't actually have anything I need to  install from this repository right now, I wanted to be sure I'm squared  away for when a time may come in the future.

After running the command I did the following to try and determine the status:

I went into synaptic > settings > repositories and looked under two of the tabs to see what was there:

The tab, "Other Sortware" Lists two entries at the bottom that stood out to me. They are:

Medibuntu - Ubuntu 11.04 "natty narwhal" (http:// packages.medibuntu.org/natty free non free) which was checked.

And:

Medibuntu (Source) - Ubuntu 11.04 "natty narwhal" (http://  packages.medibuntu.org/natty free non free) (Source Code) which was not  checked.

The tab, "Authentication" lists a total of three entries. Their descriptions are:

Ubuntu Archive Automatic Signing Key

Ubuntu CD Image Automatic Signing Key

And:

Ubuntu Extras Archive Automatic Signing Key
 
 None of those (under this Authentication tab) strike me as having  anything to do with medibuntu (could be wrong though - just not sure).
 
 Finally, I did a search in synaptic for a library I think should be  available through medibuntu, "libdvdcss." I was presented with a list of  eight items, none of them matching libdvdcss by title. The closest  match by title and description that I could identify was, "libdvdread4"  This I did as a sort of test to see if I might be accessing that  repository.
 
 Can anyone help me understand where I stand with this and what, if anything I need to do?
 
 Thanks in advance.
 
 Jake

---

### Post by wilee-nilee on 2011-04-07
If you want the key run this command, notice the matching key number at the end of the terminal info.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```

---

### Post by garvinrick4 on 2011-04-07
No Natty Medibuntu as of yet use maverick.
If you have in sources.list with natty just comment out (# in front of line)
Due out 4-28-11
[https://launchpad.net/medibuntu/+milestone/11.04](https://launchpad.net/medibuntu/+milestone/11.04)

---

### Post by garvinrick4 on 2011-04-07
Screenshot medibuntu Synaptic libdvdcss2 and keyring
Wrong screenshot.

---

### Post by garvinrick4 on 2011-04-07
Right Screenshot:
**[B]```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list [http://www.medibuntu.org/sources.list.d/$](http://www.medibuntu.org/sources.list.d/$)(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```**[/B]

---

### Post by ClientAlive on 2011-04-07
> **garvinrick4 said:**
> No Natty Medibuntu as of yet use maverick.
If you have in sources.list with natty just comment out (# in front of line)
Due out 4-28-11
[https://launchpad.net/medibuntu/+milestone/11.04](https://launchpad.net/medibuntu/+milestone/11.04)


I'm sorry garvinrick4, I don't quite understand what all of that means. I get that you are saying there is no medibuntu for 11.04, yes? Or just no packages for 11.04 in that repository? And to use the packages available for Maverick Meerkat for now? But how does that relate to accessing the repository and how does it reflect on the code wilee - nilee offered? Would that code work for me? Do I even need to do anything more based on the point I am currently at?

I suppose I could just pick something to install that wouldn't have any kind of negative impact on my machine and then uninstall it - just to test where things currently stand for me.

The thing is, I'm pretty darn new to Linux (like _maybe_ 3 weeks old). I don't fully grasp that last part of what terminal gave me (what was in the attachment) - I was just kinda going off common sense and intuition. Wish I had something a little more definitive. Maybe I'll try the install test but how do I know for certain I'm choosing something from that particular repository? And, again, if I do need to get the key, is wilee - nilee's code  good for that or is it geared toward something that does not yet exist?

Oh, and what do you mean by "comment out?" What is that?

Thx.
Jake

------------------------

Never mind about how to know I'm choosing something from that repo. I see it in your attachment now. Thx.

---

### Post by garvinrick4 on 2011-04-08
If you look in your sources.list which is your repositories you will see lines that have
look like this:
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) maverick main restricted
It is the server for ubuntu for maverick for repository main restricted. (many different servers out there)[Mirrors of Ubuntu : Ubuntu]("https://edge.launchpad.net/ubuntu/+archivemirrors")
When it does not have a # (comment sign) it is in play:
If it starts with a #(comment sign) it is not in play, (it is commented out)
The ones with 2 comment signs are telling you what the repository is.
To comment or uncomment a repository so you have to be able to change and save:
Open in root:
```
gksudo gedit /etc/apt/sources.list
```Make your changes and hit save:
To just look at and not be able to make changes and save (no root-) gksudo:
```
gedit /etc/apt/sources.list
```> I'm sorry garvinrick4, I don't quite understand what all of that means. I  get that you are saying there is no medibuntu for 11.04, yes? Or just  no packages for 11.04There are no repositories in natty for medibuntu yet, you have to use maverick.
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free
See the maverick not natty in the line following deb.
On or about 4-28-11 the medibuntu repo's for natty will be ready:
So use maverick for natty.
## You wanted to know the code in a terminal to put medibuntu repositories in your
source.list so as to be able to download packages from medibuntu. That line of code
I gave you, copy and paste it in a terminal and it will fetch it for you and install it.
If it says natty change to maverick where it says so in the line after deb because that
is the latest release of the medibuntu repo's.
In my signature there is a nice .pdf book for Ubuntu and also a how to for what ever
release you are using. Look at them both.

EDIT:* I see your sources.list you posted as a attachment it has a natty medibuntu, change it
to maverick save and:
```
sudo apt-get update
```will be fine:
Have to read all you can and follow these forums and learn. Enjoy your linux it is a nice ride.

---

### Post by ClientAlive on 2011-04-09
Right n brother. Thx. Yeah, I do have high hopes (about Linux I mean). I'm reading Ubuntu Unleashed 5th right now, actually. It's pretty good.

Have a good one.

Jake

---

### Post by ClientAlive on 2011-04-09
So I went into synaptic > settings > repositories, selected each of the entries for medibuntu under the other tab and edited each of them to change it from natty narwhal to maverick and saved. Was told I needed to reload which I did and got an error. I then ran sudo apt-get update in terminal and got a few lines talking about an error with medibuntu at the end of the list. I'm not exactly sure what needs to happen from this point but I've attached a copy and past of those lines from terminal.

Thanks so much for any help.
Jake
:D

---

### Post by garvinrick4 on 2011-04-09
Open a terminal and copy and paste this line of code:
It is just installing the key to open the repository to you.
```
sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

### Post by oldos2er on 2011-04-09
Instead of allowing unathenticated downloads, get the key: ```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783

gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

---

### Post by ClientAlive on 2011-04-09
Yup! All squared away now. Thanks.

Jake

---

