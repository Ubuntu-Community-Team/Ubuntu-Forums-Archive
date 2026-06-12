---
title: "Deb package installer thinks Blacklight is installed, but it really isn't"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Robertjm on 2008-10-05
Today I tried installing the latest version of Blacklight on Intrepid Ibex. This is a program for loading video onto a Sony Walkman mp3/mp4 player. 

I downloaded the .deb installer and made sure that all the dependencies were filled. When I run the installer it tells me its been installed. However, if I open the terminal open it says:

Unpacking replacement blacklight ...
Setting up blacklight (2.1-1) ...
chmod: cannot access '/usr/bin/blacklight2': No such file or directory

Am I supposed to have manually created that folder, or should it have been created through the .deb process?

Here's a link to their Sourceforge page.:

[https://sourceforge.net/projects/blacklight](https://sourceforge.net/projects/blacklight)
Robert

(BTW: It says replacement because I had already tried to install it and it had said successful before.)

---

### Post by wgrant on 2008-10-05
> **Robertjm said:**
> Today I tried installing the latest version of Blacklight on Intrepid Ibex. This is a program for loading video onto a Sony Walkman mp3/mp4 player. 

I downloaded the .deb installer and made sure that all the dependencies were filled. When I run the installer it tells me its been installed. However, if I open the terminal open it says:

Unpacking replacement blacklight ...
Setting up blacklight (2.1-1) ...
chmod: cannot access '/usr/bin/blacklight2': No such file or directory

Am I supposed to have manually created that folder, or should it have been created through the .deb process?

Here's a link to their Sourceforge page.:

[https://sourceforge.net/projects/blacklight](https://sourceforge.net/projects/blacklight)
Robert

(BTW: It says replacement because I had already tried to install it and it had said successful before.)

That's a bug in their package. Ask them - we can do nothing about it.

---

### Post by lithorus on 2008-10-06
It seems there is just a problem with re-installing the package. Have you tried assuming that it really is installed?

---

### Post by inportb on 2008-10-06
Also, /usr/bin/blacklight2 sounds more like an executable file than a directory.

---

