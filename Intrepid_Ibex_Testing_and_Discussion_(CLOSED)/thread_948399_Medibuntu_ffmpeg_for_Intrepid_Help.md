---
title: "Medibuntu ffmpeg for Intrepid Help?"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by martynp on 2008-10-15
Hi All,

After recently updating (well, fresh installing) to Intrepid Beta I went to use my trusted mp4ize script to convert some .avi files to .mp4 for my iPhone.

On getting the 'Unknown Codex xvid' (or libxvid) error I started delving into google and these forums to see why, and how I could fix this.

After nothing coming to hand I compiled the lastest version of ffmpeg as shown elsewhere on these forums correctly but was still getting the error. It was at this point that I noticed in synaptic that my version of ffmpeg (even after compiling and installing the latest SVN) was showing as the 'Ubuntu'one and not the 'Medibuntu' one even though I have the medibuntu repos activated and updated.

I thought perhaps I had some corruption somewhere so I did another fresh install this morning and added the Medibuntu repos straight after the first startup but STILL the ffmpeg version is the 'Ubuntu' one.

On my other machine (running Hardy) the correct Medibuntu ffmpeg is installed and shows in Synaptic enabling me to encode my video's to mp4.

Can anyone explain what is going on here? I would like the 'risky' version of ffmpeg in my Intrepid Beta install so I can encode on this machine. 

Is this possible? Can anyone point me in the right direction here?

Many Thanks in advance.

---

### Post by m94mni on 2008-10-15
Do you use the hardy or intrepid versions of the medibuntu repos?

---

### Post by martynp on 2008-10-15
Sorry, I didn't include that in my post..........

I am using the [COLOR="Red"]Intrepid[/COLOR] version... added thus:

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Thanks

---

### Post by dinxter on 2008-10-15
has ffmpeg been pulled from the medibuntu intrepid repository for some reason? there seems to be no sign of newer builds and the package seems only availiable for hardy and below

---

### Post by martynp on 2008-10-15
This is what I am thinking has happened :confused::(:mad:

Gutted......... not going back to Hardy but need a solution!

Having to use mencoder which is waaaaaaaaaaaay slower!

Anyone got any ideas?

---

### Post by dinxter on 2008-10-15
not sure what the problem is with medibuntu, might just be temporary. [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) is the debian equivalent which might be compatible enough to use its ffmpeg packages instead, maybe. or if you have time on your hands you can try bazaaring the medibuntu package at [https://code.launchpad.net/~medibuntu-maintainers/medibuntu/ffmpeg-medibuntu.intrepid](https://code.launchpad.net/~medibuntu-maintainers/medibuntu/ffmpeg-medibuntu.intrepid)

---

### Post by FuturePilot on 2008-10-15
The Medibuntu people simply haven't updated their version of ffmpeg to supersede the Ubuntu version. If you look at the ffmpeg versions you'll see there is a newer version that is coming from the Ubuntu repos.

---

### Post by martynp on 2008-10-15
Yep... can see that.

Wonder how we can give them a nudge?

---

### Post by FakeOutdoorsman on 2008-10-15
In my opinion, your best bet at this point is to compile ffmpeg yourself.  Although my suggestion is slightly selfish since I haven't done any Intrepid testing for:

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by FuturePilot on 2008-10-25
It looks like ffmpeg was removed from the Intrepid Medibuntu repos. Not sure why. 
[http://packages.medibuntu.org/intrepid/index.html]("http://packages.medibuntu.org/intrepid/index.html")
And now I can't encode certain stuff because of this unknown encoder xvid error.
:confused:

---

### Post by woyzeckswoe on 2008-10-26
im also having problems with floola for my ipod nano after upgrading to intrepid!anyone tried compiling by himself?

thanks!
hope they put it back in soon

---

### Post by mc4man on 2008-10-27
did you try installing the 'unstripped' versions of libav* ? (in synaptic

[https://bugs.launchpad.net/medibuntu/+bug/269997](https://bugs.launchpad.net/medibuntu/+bug/269997)

[https://launchpad.net/ubuntu/+source/ffmpeg/3:0.svn20080206-12ubuntu3+unstripped5](https://launchpad.net/ubuntu/+source/ffmpeg/3:0.svn20080206-12ubuntu3+unstripped5)

---

### Post by FuturePilot on 2008-10-27
> **mc4man said:**
> did you try installing the 'unstripped' versions of libav* ? (in synaptic

[https://bugs.launchpad.net/medibuntu/+bug/269997](https://bugs.launchpad.net/medibuntu/+bug/269997)

[https://launchpad.net/ubuntu/+source/ffmpeg/3:0.svn20080206-12ubuntu3+unstripped5](https://launchpad.net/ubuntu/+source/ffmpeg/3:0.svn20080206-12ubuntu3+unstripped5)

I installed all the libav* +unstripped versions but I'm still getting an error about xvid. It looks like there's an +unstripped version of ffmpeg by that second link, but I see no such version in the repos. This is what I have

3:0.svn20080206-12ubuntu3

I don't see any ffmpeg+unstripped

---

### Post by gecka on 2008-10-28
> **FuturePilot said:**
> I installed all the libav* +unstripped versions but I'm still getting an error about xvid. It looks like there's an +unstripped version of ffmpeg by that second link, but I see no such version in the repos. This is what I have

3:0.svn20080206-12ubuntu3

I don't see any ffmpeg+unstripped

Same here. I hate loosing functionnality on os upgrade.

Where is that ffmpeg-unstripped ?

---

### Post by srix on 2008-10-30
If you have the medibuntu repo enabled, you could try this (it worked for me):

1. Open Synaptic Package Manager

2. Search for and click on ffmpeg package in the list

3. Select "Package -> Force Version..." (or press Ctrl+E)

4. In the dialog that appears, the drop down list should show 2 packages - 1 from Ubuntu and 1 from Medibuntu (3:0.svn20080206-12ubuntu1+medibuntu2). Choose the "medibuntu" package and click on "Force Version"

5. Repeat the above steps for all ffmpeg support packages (libavutil, libpostproc, libswscale, libavdevice etc)

6. Click on Apply and upgrade the packages.

The problem I have with this is that when doing a system upgrade, the ffmpeg packages revert back to the Ubuntu versions, so on each upgrade I have to first de-select these packages.

HTH...

---

### Post by martynp on 2008-10-30
I thought this was going to be the answer to all my woes.

I am on Intrepid (up to date) and follwing these instructions the 'Force Package' option is greyed out!  :(

---

### Post by billhung on 2008-10-30
second the experience of martynp.

I also tried getting the hardy (8.04) package, but it's not working for intrepid (8.10).

---

### Post by raggari on 2008-10-30
> **gecka said:**
> Same here. I hate loosing functionnality on os upgrade.

Where is that ffmpeg-unstripped ?

There is no meta package for ffmpeg-unstripped. You should replace all meta package dependencies individually. Packages are:
[http://packages.ubuntu.com/search?keywords=unstripped&searchon=names&suite=all&section=all]("http://packages.ubuntu.com/search?keywords=unstripped&searchon=names&suite=all&section=all")

---

### Post by mr_pouit on 2008-10-30
Hi,

> **gecka said:**
> Same here. I hate loosing functionnality on os upgrade.

Where is that ffmpeg-unstripped ?

These are the following packages:

libavcodec-unstripped-51
libavdevice-unstripped-52
libavformat-unstripped-52
libavutil-unstripped-49
libpostproc-unstripped-51
libswscale-unstripped-0

They should include all codecs that were previously included in the Medibuntu package (except amr, but that's another topic).

---

### Post by mr_pouit on 2008-10-30
> **FuturePilot said:**
> I installed all the libav* +unstripped versions but I'm still getting an error about xvid.

Try 'libxvid' instead of 'xvid' (but you first need to install the unstripped variant of ffmpeg libs).

---

