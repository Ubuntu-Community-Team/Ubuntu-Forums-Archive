---
title: "Burning large files above 4GB to DVD"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by tedrogers on 2007-02-03
Hi Ubuntuans,

I've been trying to burn a large 4GB file onto DVD. This is a system backup that I made using partimage. I know that the file is smaller than a single layer DVD of 4.7GB.

Trouble is that none of the applications I've tried will let me burn it. The simple Nautilus burner just makes me a drinks coaster, gnome baker refuses to select the file, and the pimp-daddy burner, k3b, reports to me that it is not possible to burn files over 4GB in a dialog box and won't continue.

I don't really want to fork out $19.99 for Nero Linux - and by all accounts it's not as good as k3b anyway.

So how can I get around this problem?

I hear that there is some issue with UDF burning in ubuntu? Is this true cos this is what I need the burning apps to do?

I have dvd+rw-tools, mkisofs and udftools all installed....and k3b acknowledges that the relevant ones are present in the program list within the application.

I suppose one clumsy solution would be to create a tarball and split up the archive into smaller more palatable chunks. 

Another would be to use something like explore2fs and burn the damn thing in XP....but I don't want to go back to using XP (although I have kept the partition just for these sorts of issues).

I don't have any external firewire drives I can use, nor any massive pen drives...so I'm pretty stumped.

I suppose I could always chuck another old hard disk in, format it and copy the stuff over, but these solutions just seem like a big ol' pain in the arse.

Any suggestions anyone?

Thanks in advance.

---

### Post by mikewhatever on 2007-02-03
It looks like the answer in no. [READ HERE]("http://ubuntuforums.org/showthread.php?t=351949&highlight=udf")

---

### Post by tedrogers on 2007-02-03
Well thanks anyway...at least now I know I'm barking up the wrong tree.

Hopefully this UDF bug of 1GB limit will get fixed in some future release.

I wonder if Fedora Core Zod does a similar thing?

Anyway, I did a workaround by splitting the files into 1024MB chunks within partimage...and I'm burning to DVD as I type this.

It's amasing how you can waste nearly an entire day doing these sorts of activities :)

Thanks.

---

### Post by kung fu buntu on 2007-10-24
What is the current status of this embarassing bug for the rest of the linuxers here?

Unfortunately for me I'm still stuck in the stone age... I can't burn anything bigger than 4GB (It allows for files > 3GB).

**K3B 1.0.3**: "It is not possible to add files bigger than 4.0 GB"
**GnomeBaker 0.6**: ".... File /XXX.iso is too large - ignoring :-( write failed: Input/output error"

These are the kind of things that make me wonder if developers do "use" their computers...

Regarding the [thread ]("http://ubuntuforums.org/showthread.php?t=351949&highlight=udf") mentioned above, it is now told that the bug in udftools is fixed. Hmm... I don't even have udftools installed. So where does k3b (and gnomebaker) fit in?

[Help me!]("http://keyboardsonfire.net/img/halp.jpg") I need to burn files greater than 4GB.

Thanks!

---

### Post by tapted on 2008-01-10
Looks like this is now fixed, anyone googling this.

mkisofs is fairly instructive when you try burning files >4GB:

```
mkisofs -o ../2.iso capture002.dv 
File capture002.dv is larger than 4GiB-1.
-allow-limited-size was not specified. There is no way do represent this file size. Aborting.
This size can only be represented in the UDF filesystem.
```

This should lead you to the answer, being:

```
mkisofs -allow-limited-size -udf -o ../2.iso capture002.dv 
```

then burn with your favourite ISO burner, or cdrecord, e.g.:

```
cdrecord -verbose -dao -driveropts=burnfree 2.iso 
```

The result is a DVD-R that works fine in Linux and Windows.

At this stage, for me, the first step does not yet work in any of xcdroast, nautilus, brasero or gnomebaker. However, there's a more recent version of brasero I haven't tried.

---

### Post by freak_lick on 2008-01-27
I just don't understand why is problem in ubuntu to burn files larger than 4gb??
I used other distros and with k3b there wasn't any problem burning files larger than 4gb.
I am downloading .mkv movies which can fit on dvd, but why the hack it won't burn on ubuntu??

---

### Post by freak_lick on 2008-01-27
I have updated k3b to 1.0.4 (added gutsy-backport updates) and now i can burn files larger than 4GB!

---

### Post by fyo on 2008-02-18
> **tapted said:**
> Looks like this is now fixed, anyone googling this.

...

This should lead you to the answer, being:

mkisofs -allow-limited-size -udf -o ../2.iso capture002.dv [/CODE]


This is incorrect as the mkisofs application has NO SUCH OPTION (-allow-limited-size). The syntax you specify is that of genisoimage.

The source of the confusion is the cdrtools licensing controversy, which spawned Debian maintainers to fork cdrtools, creating cdrkit. The cdrkit version of mkisofs is called genisoimage.

The whole affair is very confusing and I, for one, am completely unable to tell where real concerns end and pure pigheadedness begins.

The practical implications are aggravated by some linux distributions symlinking mkisofs to genisoimage.

**Ubuntu does not do this, however.** (At least in Gutsy).

Anyway, I've been struggling with writing images larger than 4GB, just like everyone else. I tried using the real mkisofs with the "-iso-level 3" (and 4) option to enable support for files larger than 4GB. **I was unsuccessful!** That is, I tried mounting the image (mount -o loop isoimagefile mountpoint) and running md5sum on the large file. That failed, returning "Input/output error". I see no reason why I should coaster a DVD trying to confirm the mount findings, but anyone is welcome to try for themselves.

The solution, for me at least, is to use genisoimage with the option you suggested.

**genisoimage -allow-limited-size -udf -o isoimagefile myverylargefile**

The new version of k3b (1.04) available in the backports repository is able to burn these files as well, providing a "sufficient" version of mkisofs OR genisoimage is installed (I have no idea which on it actually uses when both are available).

In summary, I've confirmed the following methods to create DVDs with files larger than 4GB:

genisoimage with the -allow-limited-size option.
k3b 1.04 available from the backports repository
Nero Linux

---

### Post by fyo on 2008-02-18
To clarify a previous uncertainty:

K3b uses genisoimage if both genisoimage and mkisofs are installed (at least with the versions from Gutsy). It *claims* to use mkisofs:

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

but if you check the command line given at the bottom of the debug output, it clearly says genisoimage (with the -allow-limited-size option).

---

