---
title: "Building .deb files with &quot;apt-get source&quot;"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by tom purl on 2006-09-25
I need to install a program using compilation flags that weren't used when building the official Ubuntu binary version.  I know that I can do this by downloading the source, doing the "./configure; make; sudo make install" three-step.  What I would like to know is whether I *should* be doing this using the "apt-get source" command.

I read the Debian docs for this command, and the use case that they mention is one where you want to compile a version of a package from a newer version of Ubuntu/Debian than you're using.  They don't mention anything about changing compilation flags.  

So I guess this is my question:  Is there some sort of special way that you can change the compilation flags of a Debian/Ubuntu source package and still build a .deb file without using some tool like checkinstall?

Thanks in advance for any help!

Tom Purl

---

