---
title: "Can't install gnome-subtitles"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2009-01-12
Hi folks, I wonder if anyone can confirm this?

$ sudo aptitude install gnome-subtitles
```

Reading package lists... Done                         
Building dependency tree                              
Reading state information... Done                     
Reading extended state information                    
Initializing package states... Done                   
The following packages are BROKEN:                    
  libart2.24-cil libgconf2.24-cil libgnome-vfs2.24-cil libgnome2.24-cil 
The following NEW packages will be installed:                           
  gnome-sharp2{a} gnome-sharp2-examples{a} gnome-subtitles gtk-sharp2{a} 
  gtk-sharp2-examples{a} gtk-sharp2-gapi{a} libgtkhtml3.16-cil{a} monodoc-base{a} 
  monodoc-browser{a} monodoc-gtk2.0-manual{a} monodoc-manual{a}                   
0 packages upgraded, 15 newly installed, 0 to remove and 0 not upgraded.          
Need to get 10,6MB of archives. After unpacking 17,7MB will be used.              
The following packages have unmet dependencies:                                   
  libgconf2.24-cil: Conflicts: libgconf2.0-cil but 2.20.1-1ubuntu1 is installed.  
  libgnome2.24-cil: Conflicts: libgnome2.0-cil but 2.20.1-1ubuntu1 is installed.  
  libart2.24-cil: Conflicts: libart2.0-cil but 2.20.1-1ubuntu1 is installed.
  libgnome-vfs2.24-cil: Conflicts: libgnome-vfs2.0-cil but 2.20.1-1ubuntu1 is installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnome-sharp2 [Not Installed]
gnome-sharp2-examples [Not Installed]
gnome-subtitles [Not Installed]
libart2.24-cil [Not Installed]
libgconf2.24-cil [Not Installed]
libgnome-vfs2.24-cil [Not Installed]
libgnome2.24-cil [Not Installed]

Score is -9825

Accept this solution? [Y/n/q/?]

```

---

