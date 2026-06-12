---
title: "Instalar Code::Blocks offline"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by luigisrs on 2008-08-14
Hola, tengo una duda, necesito instalar Code::Blocks para la escuela, pero el problema es que allá no hay conexión a internet, me podrían ayudar con instrucciones de lo que necesito para instalar el IDE sin conexión a internet?

gracias.

Hi, I have a problem, i need to install code::blocks for school, but the problem is that we don't have a ISP @ school, so my doubt is if you can help me to get instructions to install Code::Blocks IDE without an internet conection.

Thanks

---

### Post by kflorek on 2008-08-15
Codeblocks is not on the Ubuntu DVD or CD, so you have to get it from the internet, so I'm not sure what you mean.

I assume you have internet access somewhere, since you are putting this message on this forum, and that you can put some files on a CD or a flash drive. Then you have to download the files from some site. This works for me:


wget -c [http://lgp203.free.fr/ubuntu/../pool/codeblocks/codeblocks_8.02svn5182-0ubuntu1~hardy_i386.deb](http://lgp203.free.fr/ubuntu/../pool/codeblocks/codeblocks_8.02svn5182-0ubuntu1~hardy_i386.deb)
wget -c [http://lgp203.free.fr/ubuntu/../pool/codeblocks/libcodeblocks0_8.02svn5182-0ubuntu1~hardy_i386.deb](http://lgp203.free.fr/ubuntu/../pool/codeblocks/libcodeblocks0_8.02svn5182-0ubuntu1~hardy_i386.deb)
wget -c [http://lgp203.free.fr/ubuntu/../pool/codeblocks/libwxsmithlib0_8.02svn5182-0ubuntu1~hardy_i386.deb](http://lgp203.free.fr/ubuntu/../pool/codeblocks/libwxsmithlib0_8.02svn5182-0ubuntu1~hardy_i386.deb)
wget -c [http://lgp203.free.fr/ubuntu/../pool/codeblocks/codeblocks-contrib_8.02svn5182-0ubuntu1~hardy_i386.deb](http://lgp203.free.fr/ubuntu/../pool/codeblocks/codeblocks-contrib_8.02svn5182-0ubuntu1~hardy_i386.deb)
wget -c [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/libwxbase2.8-0_2.8.8.1-0_i386.deb](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/libwxbase2.8-0_2.8.8.1-0_i386.deb)
wget -c [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/libwxgtk2.8-0_2.8.8.1-0_i386.deb](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/libwxgtk2.8-0_2.8.8.1-0_i386.deb)
wget -c [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/wx2.8-headers_2.8.8.1-0_i386.deb](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/wx2.8-headers_2.8.8.1-0_i386.deb)
wget -c [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/libwxbase2.8-dev_2.8.8.1-0_i386.deb](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/libwxbase2.8-dev_2.8.8.1-0_i386.deb)
wget -c [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/libwxgtk2.8-dev_2.8.8.1-0_i386.deb](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/libwxgtk2.8-dev_2.8.8.1-0_i386.deb)
wget -c [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/wx-common_2.8.8.1-0_i386.deb](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/wx-common_2.8.8.1-0_i386.deb)
wget -c [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/wx2.8-doc_2.8.8.1-0_all.deb](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/wx2.8-doc_2.8.8.1-0_all.deb)
wget -c [http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/wx2.8-i18n_2.8.8.1-0_all.deb](http://apt.wxwidgets.org/dists/hardy-wx/main/binary-i386/wx2.8-i18n_2.8.8.1-0_all.deb)

or put this in a text file after:

#!/bin/sh

and run it.

 The codeblock files are on the site at

[http://lgp203.free.fr/pool/codeblocks](http://lgp203.free.fr/pool/codeblocks)

but you can't read the full names of the files the way the guy did it.

 The wx files are at

[http://apt.wxwidgets.org](http://apt.wxwidgets.org)

Otherwise you could find the repository and instructions for adding it to apt by looking it up on google. Then get the files with apt or synaptic, and then the files will also show up in /var/cache/apt/archive

Clicking on the files one by one as they are listed in this message also seems to work.

Good luck.

---

### Post by luigisrs on 2008-08-15
> Codeblocks is not on the Ubuntu DVD or CD, so you have to get it from the internet, so I'm not sure what you mean.

I ment that if I can download from somewhere all the needed files to intall code::blocks in a computer without a internet conection :???: Sorry, I'm still kind of a newbie...

---

