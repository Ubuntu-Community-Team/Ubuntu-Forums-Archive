---
title: "HAL .fdi files--the new Xorg configure"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-10-14
Well--I think that I've got enough info to start spreading it around :)

I was getting random non-detect of my USB Saitek keyboard & USB cordless Trackman Wheel--So I went to Gentoo Wiki & searched for more info ;) 

I have created .fdi files for both my keyboard (with my favored xorg options) & a basic file to make sure my Trackman gets "found"

First some links: [http://www.freedesktop.org/wiki/Software/hal](http://www.freedesktop.org/wiki/Software/hal)
                         [http://gentoo-wiki.com/HAL](http://gentoo-wiki.com/HAL)
and the most important one: [http://gentoo-wiki.com/X11_Mouse/Xorg_7.3](http://gentoo-wiki.com/X11_Mouse/Xorg_7.3)
Look at Advanced Topics :)
The "book": [http://people.freedesktop.org/~david/hal-spec/hal-spec.html](http://people.freedesktop.org/~david/hal-spec/hal-spec.html)

With a small amount of expermenting I created these files:

/etc/hal/fdi/policy/99-x11-mouse.fdi

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <merge key="input.x11_options.Emulate3Buttons"type="string">True</merge>
    </match>
  </device>
</deviceinfo>

/etc/hal/fdi/policy/99-x11-keyboard.fdi

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.keyboard">
      <merge key="input.x11_options.XkbRules" type="string">xorg</merge>
      <merge key="input.x11_options.XkbModel" type="string">macintosh</merge>
      <merge key="input.x11_options.XkbLayout" type="string">us</merge>
    </match>
  </device>
</deviceinfo>

If you want to do ZAxisMapping for your mouse--remember to use "integer" instead of "string"--another type is "bool"--that can be used instead of "string"

I'm still looking at ways to make this work--have talked with a couple of other guys about mapping--anything anyone wants to add--I think this would be a good place for it.....

If anyone wants the "real" copies of my files for reference--just ask.

---

### Post by wgrant on 2008-10-14
See also [the Ubuntu wiki page](https://wiki.ubuntu.com/X/Config#hal).

---

### Post by autocrosser on 2008-10-14
Yes--I looked there first--wanted more info--hence this post ;)

---

### Post by incubus on 2008-10-14
autocrosser,

Thanks for starting this.  I agree with you and as I said elsewhere, I think this change is going to catch a lot of people by surprise.  I think we should try as hard as possible to update the Ubuntu Wiki with some good explanations on how to do this (mimicking the Gentoo Wiki).  There's currently this page:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

but honestly, I think it needs a lot of polishing.


One thing, are you sure you need to use integer or boolean for some options?  I thought I read somewhere that x11 options are always strings.  Maybe I read it here:

[http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi](http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi)

Please correct me if I'm wrong.


By the way, another way to set up inputs is via xinput, which I personally like.  That was not working on x86_64, but William Grant just put on a patch to fix it.

Thanks again,

incubus

---

### Post by incubus on 2008-10-14
> **autocrosser said:**
> Yes--I looked there first--wanted more info--hence this post ;)

Having the information on the Wiki is nice, in my opinion, because other people can edit it.  I've seen many great tutorials on ubuntuforums that get outdated because the original poster stops maintaining it.  What do you think?

---

### Post by autocrosser on 2008-10-14
I'm not sure about the "bool' or "integer" right now--need to do more reading & if anyone knows where to read this info from HAL---please post it--HAL feedback as to if a tweak has worked is good:)

> **incubus said:**
> autocrosser,

Thanks for starting this.  I agree with you and as I said elsewhere, I think this change is going to catch a lot of people by surprise.  I think we should try as hard as possible to update the Ubuntu Wiki with some good explanations on how to do this (mimicking the Gentoo Wiki).  There's currently this page:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

but honestly, I think it needs a lot of polishing.


One thing, are you sure you need to use integer or boolean for some options?  I thought I read somewhere that x11 options are always strings.  Maybe I read it here:

[http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi](http://cgit.freedesktop.org/xorg/xserver/tree/config/x11-input.fdi)

Please correct me if I'm wrong.


By the way, another way to set up inputs is via xinput, which I personally like.  That was not working on x86_64, but William Grant just put on a patch to fix it.

Thanks again,

incubus

---

### Post by autocrosser on 2008-10-14
I think that we could "polish" the info here a bit & then update the Wiki when it looks good----I for one need to do a bit of reading & we could get some "case studies" of what works for what hardware--like Gentoo Wiki....

---

### Post by wgrant on 2008-10-14
> **incubus said:**
> autocrosser,

Thanks for starting this.  I agree with you and as I said elsewhere, I think this change is going to catch a lot of people by surprise.  I think we should try as hard as possible to update the Ubuntu Wiki with some good explanations on how to do this (mimicking the Gentoo Wiki).  There's currently this page:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

but honestly, I think it needs a lot of polishing.

I plan to rework that page before Intrepid's release. I'm considering splitting it into separate display and input pages and possibly even have separate Intrepid and pre-Intrepid pages, due to the large changes.

---

### Post by autocrosser on 2008-10-15
Sounds good--what else do you need?

---

### Post by incubus on 2008-10-15
> **wgrant said:**
> I plan to rework that page before Intrepid's release. I'm considering splitting it into separate display and input pages and possibly even have separate Intrepid and pre-Intrepid pages, due to the large changes.

William,

I think that's a good idea.  Perhaps we could have an introductory section with a simple example, in tutorial style, to give a general idea.  Then we can put some more concrete and specific examples either after that or in separate pages.

The idea is that a typical person would just need to read the introduction and then look for a specific page for his or her issue, if necessary at all.  What do you think?

I'll be checking the page to help proof-read.  If you'd like to delegate some tasks, feel free to give us orders.  : )

incubus

---

### Post by wgrant on 2008-10-15
> **incubus said:**
> William,

I think that's a good idea.  Perhaps we could have an introductory section with a simple example, in tutorial style, to give a general idea.  Then we can put some more concrete and specific examples either after that or in separate pages.

The idea is that a typical person would just need to read the introduction and then look for a specific page for his or her issue, if necessary at all.  What do you think?

That was my intention, yes. I'm busy with uni stuff until Friday, so can't think a whole lot about it until then.

---

### Post by autocrosser on 2008-10-19
wgrant--looks like this thread should be sticky--I think quite a large number of people will be needing this info very soon....

---

### Post by autocrosser on 2008-10-19
I am bumping this to keep on top until the thread becomes sticky.

---

### Post by autocrosser on 2008-10-19
bump

---

### Post by gaelfx on 2008-10-19
I read your response to Tielie, and his response to you [http://ubuntuforums.org/showthread.php?t=892666&highlight=login]("http://ubuntuforums.org/showthread.php?t=892666&highlight=login"), so first let me say that I know helping people is tough, and I am glad that you are having a serious discussion about how best to do that.

Secondly, I have to ask if there isn't an easier way to auto-generate those .fdi files, I have no idea how to write XML code properly, though I'm sure if I spent enough time with your directions, I would figure it out, but the thing is: I don't have that much time right now. I'm having the same problem as Tielie, I get to login screen and there is no mouse or keyboard input EXCEPT alt+f2. I understand the usefulness of HAL in this situation, anything that prevents restarting of xserver is glorious imo, but it seems like there should be a simpler solution?

Perhaps I'm over-complicating the issue in my head before I even try it, but I would be much more comfortable if there were a way to make my computer do this work for me since I trust its typing skills more than mine. So I guess my question is this: could I use the .fdi's you posted as a template for fixing my problem, or do I have to generate wholly new ones for my particular hardware?

Thanks again for sharing this VERY useful information (I was trying to edit my remarkably sparce xorg.conf before I saw this thread)

---

### Post by wgrant on 2008-10-19
> **gaelfx said:**
> I read your response to Tielie, and his response to you [http://ubuntuforums.org/showthread.php?t=892666&highlight=login]("http://ubuntuforums.org/showthread.php?t=892666&highlight=login"), so first let me say that I know helping people is tough, and I am glad that you are having a serious discussion about how best to do that.

Secondly, I have to ask if there isn't an easier way to auto-generate those .fdi files, I have no idea how to write XML code properly, though I'm sure if I spent enough time with your directions, I would figure it out, but the thing is: I don't have that much time right now. I'm having the same problem as Tielie, I get to login screen and there is no mouse or keyboard input EXCEPT alt+f2. I understand the usefulness of HAL in this situation, anything that prevents restarting of xserver is glorious imo, but it seems like there should be a simpler solution?

Perhaps I'm over-complicating the issue in my head before I even try it, but I would be much more comfortable if there were a way to make my computer do this work for me since I trust its typing skills more than mine. So I guess my question is this: could I use the .fdi's you posted as a template for fixing my problem, or do I have to generate wholly new ones for my particular hardware?

Thanks again for sharing this VERY useful information (I was trying to edit my remarkably sparce xorg.conf before I saw this thread)

It sounds to me like you won't fix your problem by editing fdi files. Make sure that you have xserver-xorg-input-all installed.

---

### Post by autocrosser on 2008-10-20
bump--until this is sticky

---

### Post by jbg7474 on 2008-10-24
BUMP, again.  Great googly moogly, this REALLY needs to be sticky!!  I've been beating my head against a wall trying to get button mapping to stick for my mouse.

---

