---
title: "No encoding AAC in ffmpeg &amp; no MP4 support in x264 package"
date: 2010-01-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2010-01-01
I know the lack of encoding AAC in ffmpeg was raised in Karmic, but if that's down to licencing, then ffmpeg should be in a different repository and not had AAC support removed.

As for x264 package, MP4 support was not compiled in. The last release it did was Jaunty. A bug was raised: [bug 464797]("https://bugs.launchpad.net/ubuntu/+source/x264/+bug/464797")

I'm resorting to using packages from Jaunty, but this is not ideal as these packages are out of date.

---

### Post by SuperSonic4 on 2010-01-01
Why not compile x264 with mp4 support?

```
./configure --prefix=/usr/local --enable-mp4-output --enable-pthread --enable-pic --enable-shared
```

ffmpeg can also be compiled with AAC easily enough

---

### Post by mc4man on 2010-01-01
If you're not inclined to [build them]("http://ubuntuforums.org/showthread.php?t=786095"), then add the karmic medibuntu repo which has enabled aac in the ffmpeg libs. (for use in the ubnutu repo apps and ffmpeg

Or do both, add medibuntu for aac enabled shared libs, and then build a x264 and a standalone static ffmpeg for using ffmpeg itself and or building off of.

Atm karmic and lucid use the same ffmpeg version, and it's possible lucid will release with that version (unfortunate but a good possibility

Edit: sorry, adding the karmic medibuntu won't work, lucid now showing a ...ubuntu4 which is a higher versioning than the medibuntu ...3...

---

### Post by FakeOutdoorsman on 2010-01-01
Perhaps the best method for those who don't want to compile is to ask Medibuntu to offer a **libavcodec-extra-52** package for Lucid.  This has already been done for Karmic:

[Wishlist: create ffmpeg with aac/libfaac support for Karmic](https://bugs.launchpad.net/medibuntu/+bug/490227)

Is it more appropriate to make a new Wishlist request for a Lucid **libavcodec-extra-52**, or to append to this Karmic one?

---

### Post by mc4man on 2010-01-01
> Is it more appropriate to make a new Wishlist request for a Lucid libavcodec-extra-52

Better to do a new one I'd think, plus get it confirmed by someone else

Edit: not sure whether wishlists need to be confirmed, bugs do ( that silly ubuntu-restr.... bug, which was marked improperly as 'fix released' and then re-marked as new by me is going to sit there doing nothing nothing till confirmed ( I've basically given up there...

---

### Post by FakeOutdoorsman on 2010-01-01
> **mc4man said:**
> Better to do a new one I'd think, plus get it confirmed by someone else

Edit: not sure whether wishlists need to be confirmed, bugs do ( that silly ubuntu-restr.... bug, which was marked improperly as 'fix released' and then re-marked as new by me is going to sit there doing nothing nothing till confirmed ( I've basically given up there...

I made a new one, and apparently a wishlist is a bug report:
[url=https://bugs.launchpad.net/medibuntu/+bug/502209]
Wishlist: create libavcodec-extra-52 and friends for Lucid[/url]

**Update:** I confirmed your **ubuntu-restricted-extras** bug:
[Bug #462366 in ubuntu-restricted-extras (Ubuntu): &#8220;ubuntu-restricted-extras installs stripped ffmpeg libraries&#8221;](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/462366)

---

### Post by FakeOutdoorsman on 2010-01-01
Hmm...maybe I acted too early as the Karmic report has a "also affects Lucid".  Oh well.  Better than nothing.

---

### Post by mc4man on 2010-01-01
> maybe I acted too early...
No harm there, it may end up a dup.

As far as the other - thanks, am curios to see ... It's a bit of circular 'logic' that escapes me
commit in august causes bug, fix released is the commit in august that caused bug, ect., ect.

there does seem to be a bit of 'attention' paid to faac/faad, for a while aac **decoding** was disabled in lucid's xine-libs, again went around in a bit of a circle till it was re-enabled

[https://bugs.launchpad.net/baltix/+bug/496010](https://bugs.launchpad.net/baltix/+bug/496010)

Edit: did do a quick re-build of medibuntu's source for lucid to see if any issues, none, so quite do-able.

They might want to wait to see what lucid is going to release with, should be apparent fairly soon - next several weeks or so.

---

### Post by phenest on 2010-01-08
> **FakeOutdoorsman said:**
> Perhaps the best method for those who don't want to compile is to ask Medibuntu to offer a **libavcodec-extra-52** package for Lucid.  This has already been done for Karmic:

[Wishlist: create ffmpeg with aac/libfaac support for Karmic](https://bugs.launchpad.net/medibuntu/+bug/490227)

Is it more appropriate to make a new Wishlist request for a Lucid **libavcodec-extra-52**, or to append to this Karmic one?

I don't know why this can't simply be sorted out in Lucid's repository rather than have to use Medibuntu's.

Also, should this need a WishList? These features should have never been removed.

---

### Post by mc4man on 2010-01-08
> I don't know why this can't simply be sorted out in Lucid's repository rather than have to use Medibuntu's.

Also, should this need a WishList? These features should have never been removed.

simple explanation  - it's not coming back unless ffmpeg changes it's ' position' on faac (libfaac) - "non-free"

So either hope medibuntu picks it up for lucid (lend your support to posted wishlist if desired) or build your own ffmpeg or live with it.

---

### Post by FakeOutdoorsman on 2010-01-08
> **phenest said:**
> I don't know why this can't simply be sorted out in Lucid's repository rather than have to use Medibuntu's.
I'm not too sure on how these license issues work out, but it was determined (for now) that *libfaac* was non-free and including it would have caused FFmpeg to be non-free and unredistributable.  To the end user this is quite annoying and disruptive, and to the packager it must be equally frustrating.

There may be a better method, but I'm not very experienced with the whole packaging thing.

---

### Post by phenest on 2010-01-08
> **FakeOutdoorsman said:**
> ...it was determined (for now) that *libfaac* was non-free and including it would have caused FFmpeg to be non-free and unredistributable.  To the end user this is quite annoying and disruptive...

Surely there are other packages that are non-free that are in the repository's?

I do a lot of video encoding in MP4 format, and to be able to encode x264 but not in an MP4 container is very disruptive.

---

### Post by seeker5528 on 2010-01-08
Hmm, libfaac and libfaad are still in universe/multiverse, so I would think the aac encoding would work. I have some .m4a files that I play with no problems, never had a reason to want to encode with aac for stuff I am encoding myself, so I can't vouch for that.

The x264 package seems to still be in universe as well.

Do these things not work, or is the complaint that they don't work out of the box?

[http://packages.ubuntu.com/search?keywords=libfaa&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=libfaa&searchon=names&suite=lucid&section=all)
[http://packages.ubuntu.com/search?keywords=x264&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=x264&searchon=names&suite=lucid&section=all)

Later, Seeker

---

### Post by mc4man on 2010-01-08
It's really only libacodecXX which is not going to get aac encoding enabled thru libfaac. (atm is case closed

You're certainly free to install libfaac and get aac encoding thru any number of apps and for gstreamer by installing the bad-multiverse plug-in, just not thru libavcodecXX. (or any app that uses libavcodec for aac encoding.

---

