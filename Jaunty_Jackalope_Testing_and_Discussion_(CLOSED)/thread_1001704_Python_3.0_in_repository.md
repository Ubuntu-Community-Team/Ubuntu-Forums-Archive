---
title: "Python 3.0 in repository"
date: 2008-12-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shirishagarwal on 2008-12-04
Hi all, 
 Python 3.0 was released just a day ago [http://lwn.net/Articles/309566/](http://lwn.net/Articles/309566/)

and now its being built in our repositories as we speak 

[https://edge.launchpad.net/ubuntu/+builds?build_text=python3.0&build_state=building](https://edge.launchpad.net/ubuntu/+builds?build_text=python3.0&build_state=building)

Some google reviews of python 3.0 

[http://www.linux.com/feature/150399](http://www.linux.com/feature/150399)

[http://fedoraproject.org/wiki/FWN/LatestIssue#Python_Bump_to_2.6_in_Rawhide](http://fedoraproject.org/wiki/FWN/LatestIssue#Python_Bump_to_2.6_in_Rawhide)

What effect would the new interpreter would have to ubuntu and its packages?

From what I know, we use an ensemble of C, C++, python and some Mono (in GNOME) . 

Comments, flames, suggestions all invited :)

---

### Post by Quikee on 2008-12-04
> **shirishagarwal said:**
> 
What effect would the new interpreter would have to ubuntu and its packages?


No effect at all... Python 3.0 is installed in parallel to Python 2.5 and there is not a single program in the repository written for Python 3.0.

---

### Post by RAOF on 2008-12-04
> **Quikee said:**
> No effect at all... Python 3.0 is installed in parallel to Python 2.5 and there is not a single program in the repository written for Python 3.0.

And while each minor Python version bump (2.3 -> 2.4 -> 2.5) has broken some python programs, that was purely accidental.  Python 2.x -> Python 3.0 is *meant* to break programs!

---

### Post by shirishagarwal on 2008-12-04
python 2.6 is supposed to be the one in-between. Its supposed to be backward and forward-compatible between both . It would issue warnings & stuff about code which is incompatible with the 3.0 version.

---

### Post by DougieFresh4U on 2008-12-04
> **RAOF said:**
> And while each minor Python version bump (2.3 -> 2.4 -> 2.5) has broken some python programs, that was purely accidental.  Python 2.x -> Python 3.0 is *meant* to break programs!

I have had some strange Syntex errors with python updates, (my machine and my sisters machine)
Bug# 304592

---

### Post by shirishagarwal on 2008-12-04
you need to do bracket lpbug bracketclose 304592 bracket /lpbug bracketclose and it would look like this 

[lpbug]304592[/lpbug]

---

### Post by bertilow on 2008-12-06
Will there be Python 3 packages for Hardy?

---

### Post by Metaleks on 2009-02-21
While the switch to 3.0 (as the default version) is out of the question, does 2.6 have any chance of being the default version for Jaunty? So far, version 2.5.2 is the default that comes with the system. 

I realize that every version of Python bring a chance that it could break something, but we are now a few versions behind. 

Any news on this?

---

### Post by danbuter on 2009-02-21
I bet it will be 2 or 3 years until Python 2.x is actually dropped, if ever. Too many programmers are too lazy to go back and fix their code ;).

---

### Post by pressureman on 2009-02-21
I'd like to see 2.6 replace 2.5.4 also. I realise an upgrade to 3.0 is major and would cause huge breakage, but 2.6 is backwards compatible, whilst at the same time allowing some features from 3.0 to be used, and throwing warnings about 2.x stuff that is deprecated in 3.0. That alone will be a help to developers starting to migrate to 3.0.

---

### Post by Metaleks on 2009-02-21
> **pressureman said:**
> I'd like to see 2.6 replace 2.5.4 also. I realise an upgrade to 3.0 is major and would cause huge breakage, but 2.6 is backwards compatible, whilst at the same time allowing some features from 3.0 to be used, and throwing warnings about 2.x stuff that is deprecated in 3.0. That alone will be a help to developers starting to migrate to 3.0.
This is exactly the rationale we need to have.

Is there any way we can see the default packages for Jaunty as of now?

---

### Post by pressureman on 2009-02-27
Yay! Python 2.6.1 will be the default version in Jaunty...

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000541.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000541.html)

This is just what I was hoping for :)

And of course Python 3.0.1 is available too, for those who want/need it.

---

### Post by andrewabc on 2009-02-27
> **Metaleks said:**
> Is there any way we can see the default packages for Jaunty as of now?

When I want to know what version of package(program) is in jaunty (or whatever testing version of ubuntu) I normally google "jaunty <program>"

[https://launchpad.net/ubuntu/jaunty/](https://launchpad.net/ubuntu/jaunty/)  <-click on architecture (x86 or amd64 etc), then search for what you are looking for.

---

### Post by castrojo on 2009-02-27
> **andrewabc said:**
> When I want to know what version of package(program) is in jaunty (or whatever testing version of ubuntu) I normally google "jaunty <program>

Check out [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by billstei on 2009-02-27
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Remember to set the search Distribution drop-down box to Jaunty.

---

### Post by andrewabc on 2009-02-27
I knew there was a better site.
Thanks for correcting me.

---

