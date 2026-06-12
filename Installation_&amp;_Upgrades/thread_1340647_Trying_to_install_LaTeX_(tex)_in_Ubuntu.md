---
title: "Trying to install LaTeX (tex) in Ubuntu"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by cAlpha on 2009-11-28
Downloaded and unpacked the archive *install-tl-unx.tar.gz* found on the web.

Navigated to unpacked directory, and tried to run the "install-tl" script and get back the error: 
"unusable location [http://mirror.ctan.org/systems/texlive/tlnet/tlpkg/texlive.tlpdb](http://mirror.ctan.org/systems/texlive/tlnet/tlpkg/texlive.tlpdb), could not load any packages"

I checked the referenced directory and the file in question (.../tlpkg/texlive.tlpdb) exists, so it's not simply a missing file or host issue.  

I checked the documentation and tried installing via the GUI option and get the same error.  

Anyone have ideas one how else I can get LaTeX installed on my machine?

---

### Post by jacksaff on 2009-11-28
sudo apt-get install texlive

---

### Post by cAlpha on 2009-11-28
lol, derrr.  I hadn't intended to reinvent the wheel, but evidently I was trying to.  

Thanks, dude.

Got an error at the end of installation:
"Errors encountered while processing:  msttcorefonts
E: Sub-processes /usr/bin/dpkg returned an error code (1)"

Are these going to present any issues, or should I just ignore them?

---

### Post by tinnsi on 2009-12-15
Was it resolved?  Did you get those packages in the end?  I am having the same problem, I installed texlive as suggested above, but none of the packages I had been using were understood by latex when I ran the script.  Eg pslatex is a package that my latex doesn't understand.

---

### Post by cAlpha on 2009-12-15
Yeah, 'sudo apt-get install texlive' worked for me and the errors I got haven't presented any issues.  I first got them a while back while trying to do something else and I've never been able to figure out what they correspond to.  *shrug*

---

