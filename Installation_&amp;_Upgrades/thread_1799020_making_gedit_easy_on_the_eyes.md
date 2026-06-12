---
title: "making gedit easy on the eyes"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-07-07
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

credit to [http://www.benninger.ca/?page_id=29](http://www.benninger.ca/?page_id=29) && [http://www.benninger.ca/wp-content/uploads/2010/10/omega_v0.1.tar.gz](http://www.benninger.ca/wp-content/uploads/2010/10/omega_v0.1.tar.gz)  this is for ubuntu 10.10, and is broken on 11.10 because of GTK2 going to GTK3

(no need to download as the tarball was a small script that i have hijacked and reposted for personal use)

(im totaly going to jack this code and manipulate it)

load up terminal

alt + f2

run > gnome-terminal

first things first, this is installed system wide, as such you need to install your font system wide also.  to do this you need to be root

```

sudo su

```

once in root mode drop this insanely filthy script

```

cat > /usr/share/gtksourceview-2.0/styles/omega.xml << "EOF"
<?xml version="1.0" encoding="UTF-8"?>
<style-scheme id="omega" _name="Omega" version="1.0">
<author>Christopher Benninger</author>
<_description>a scheme</_description>
<!-- Tango Palette -->
<color name="butter1" value="#fce94f"/>
<color name="butter2" value="#DEA818"/>
<color name="butter3" value="#c4a000"/>
<color name="chameleon1" value="#83C244"/>
<color name="chameleon2" value="#6EB924"/>
<color name="chameleon3" value="#4e9a06"/>
<color name="orange1" value="#fcaf3e"/>
<color name="orange2" value="#f57900"/>
<color name="orange3" value="#ce5c00"/>
<color name="skyblue1" value="#729fcf"/>
<color name="skyblue2" value="#3465a4"/>
<color name="skyblue3" value="#204a87"/>
<color name="plum1" value="#B673AF"/>
<color name="plum2" value="#75507b"/>
<color name="plum3" value="#5c3566"/>
<color name="chocolate1" value="#e9b96e"/>
<color name="chocolate2" value="#c17d11"/>
<color name="chocolate3" value="#8f5902"/>
<color name="scarletred1" value="#ef2929"/>
<color name="scarletred2" value="#cc0000"/>
<color name="scarletred3" value="#a40000"/>
<color name="aluminium1" value="#eeeeec"/>
<color name="aluminium2" value="#DBD4D4"/>
<color name="aluminium3" value="#babdb6"/>
<color name="aluminium4" value="#888a85"/>
<color name="aluminium5" value="#555753"/>
<color name="aluminium6" value="#3D3B3B"/>
<!-- Global Settings -->
<style name="text" foreground="aluminium2" background="#000000"/>
<style name="selection" foreground="aluminium1" background="aluminium4"/>
<style name="cursor" foreground="aluminium2"/>
<style name="current-line" background="aluminium5"/>
<style name="line-numbers" foreground="aluminium5" background="#black"/>
<style name="draw-spaces" foreground="aluminium4"/>
<!-- Bracket Matching -->
<style name="bracket-match" foreground="aluminium1" background="aluminium3" bold="true"/>
<style name="bracket-mismatch" foreground="aluminium1" background="scarletred2" bold="true"/>
<!-- Right Margin -->
<style name="right-margin" foreground="aluminium1" background="aluminium4"/>
<!-- Search Matching -->
<style name="search-match" foreground="aluminium1" background="chameleon3"/>
<!-- Comments -->
<style name="def:comment" foreground="aluminium4"/>
<style name="def:shebang" foreground="aluminium4" bold="true"/>
<style name="def:doc-comment-element" italic="true"/>
<!-- Constants -->
<style name="def:constant" foreground="butter2"/>
<style name="def:string" foreground="butter2"/>
<style name="def:special-char" foreground="orange3"/>
<style name="def:special-constant" foreground="orange3"/>
<style name="def:floating-point" foreground="orange3"/>
<!-- Identifiers -->
<style name="def:identifier" foreground="skyblue1"/>
<!-- Statements -->
<style name="def:statement" foreground="#white" bold="true"/>
<!-- Types -->
<style name="def:type" foreground="chameleon1" bold="true"/>
<!-- Others -->
<style name="def:preprocessor" foreground="plum1"/>
<style name="def:error" foreground="aluminium1" background="scarletred2" bold="true"/>
<style name="def:note" background="butter1" foreground="aluminium4" bold="true"/>
<style name="def:underlined" italic="true" underline="true"/>
<!-- Language specific -->
<style name="diff:added-line" foreground="butter2"/>
<style name="diff:removed-line" foreground="skyblue1"/>
<style name="diff:changed-line" foreground="plum1"/>
<style name="diff:diff-file" foreground="chameleon1" bold="true"/>
<style name="diff:location" foreground="chameleon1"/>
<style name="diff:special-case" foreground="#white" bold="true"/>
</style-scheme>
EOF
exit

```
then hit enter to exit root mode and restart gedit then load omega style

alt + f2

run > gedit

edit > prefrences > font & colors > omega

while your in there tab over to the plugins and install the file browser pane

hit f9 when gedit is running, and go down to the bottom left and click the file cabinet icon....  looks like this...

[IMG]http://img204.imageshack.us/img204/9574/gedit.jpg[/IMG]

for ubuntu 11.10 i changed the script slightly to place the file in gtk source view 3, and worked other various kinks out of the script.

load up terminal

alt + f2

run > gnome-terminal

```

sudo su

```

once in root mode drop this filthy script

```

cat > /usr/share/gtksourceview-3.0/styles/omega.xml << "EOF"
<?xml version="1.0" encoding="UTF-8"?>
<style-scheme id="omega" _name="Omega" version="1.0">
<author>Christopher Benninger</author>
<_description>a scheme</_description>
<!-- Tango Palette -->
<color name="butter1" value="#fce94f"/>
<color name="butter2" value="#DEA818"/>
<color name="butter3" value="#c4a000"/>
<color name="chameleon1" value="#83C244"/>
<color name="chameleon2" value="#6EB924"/>
<color name="chameleon3" value="#4e9a06"/>
<color name="orange1" value="#fcaf3e"/>
<color name="orange2" value="#f57900"/>
<color name="orange3" value="#ce5c00"/>
<color name="skyblue1" value="#729fcf"/>
<color name="skyblue2" value="#3465a4"/>
<color name="skyblue3" value="#204a87"/>
<color name="plum1" value="#B673AF"/>
<color name="plum2" value="#75507b"/>
<color name="plum3" value="#5c3566"/>
<color name="chocolate1" value="#e9b96e"/>
<color name="chocolate2" value="#c17d11"/>
<color name="chocolate3" value="#8f5902"/>
<color name="scarletred1" value="#ef2929"/>
<color name="scarletred2" value="#cc0000"/>
<color name="scarletred3" value="#a40000"/>
<color name="aluminium1" value="#eeeeec"/>
<color name="aluminium2" value="#DBD4D4"/>
<color name="aluminium3" value="#babdb6"/>
<color name="aluminium4" value="#888a85"/>
<color name="aluminium5" value="#555753"/>
<color name="aluminium6" value="#3D3B3B"/>
<!-- Global Settings -->
<style name="text" foreground="aluminium2" background="#000000"/>
<style name="selection" foreground="aluminium1" background="aluminium4"/>
<style name="cursor" foreground="aluminium2"/>
<style name="current-line" background="aluminium5"/>
<style name="line-numbers" foreground="aluminium5" background="#black"/>
<style name="draw-spaces" foreground="aluminium4"/>
<!-- Bracket Matching -->
<style name="bracket-match" foreground="aluminium1" background="aluminium3" bold="true"/>
<style name="bracket-mismatch" foreground="aluminium1" background="scarletred2" bold="true"/>
<!-- Right Margin -->
<style name="right-margin" foreground="aluminium1" background="aluminium4"/>
<!-- Search Matching -->
<style name="search-match" foreground="aluminium1" background="chameleon3"/>
<!-- Comments -->
<style name="def:comment" foreground="aluminium4"/>
<style name="def:shebang" foreground="aluminium4" bold="true"/>
<style name="def:doc-comment-element" italic="true"/>
<!-- Constants -->
<style name="def:constant" foreground="butter2"/>
<style name="def:string" foreground="butter2"/>
<style name="def:special-char" foreground="orange3"/>
<style name="def:special-constant" foreground="orange3"/>
<style name="def:floating-point" foreground="orange3"/>
<!-- Identifiers -->
<style name="def:identifier" foreground="skyblue1"/>
<!-- Statements -->
<style name="def:statement" foreground="#white" bold="true"/>
<!-- Types -->
<style name="def:type" foreground="chameleon1" bold="true"/>
<!-- Others -->
<style name="def:preprocessor" foreground="plum1"/>
<style name="def:error" foreground="aluminium1" background="scarletred2" bold="true"/>
<style name="def:note" background="butter1" foreground="aluminium4" bold="true"/>
<style name="def:underlined" italic="true" underline="true"/>
<!-- Language specific -->
<style name="diff:added-line" foreground="butter2"/>
<style name="diff:removed-line" foreground="skyblue1"/>
<style name="diff:changed-line" foreground="plum1"/>
<style name="diff:diff-file" foreground="chameleon1" bold="true"/>
<style name="diff:location" foreground="chameleon1"/>
<style name="diff:special-case" foreground="#white" bold="true"/>
</style-scheme>
EOF
exit

```

then hit enter to exit root mode and restart gedit then load omega style

alt + f2

run > gedit

edit > prefrences > font & colors > omega





to make gedit more of an IDE for development.....

alt + f2

gksu synaptic

run

search and find and install gedit-plugins

first off setup spell checking edit > preferences  go to the plugins tab then scroll down to spell checker and tick the box

then close the dialog, and then go to tools > highlight misspelled words

&& bug in new gedit found wont keep settings to highlight misspelled words

---

### Post by mörgæs on 2011-07-07
Thanks, I'll try that.

---

### Post by An Sanct on 2011-07-07
Nice, I'll try this!

One question tho ... is it 'non-harmful' ? I mean, after executing the script, will I be able to go back to my old "C++" like gedit scheme if I want to?

---

### Post by boblizar on 2011-07-07
the script is a cat > statement so its creating a new file/preset for gedit...

ls /usr/share/gtksourceview-2.0/styles/

&& compare it to

gedit > edit > preferences > fonts & colors

(its simply adding another preset to your fonts and colors to chose from)

(i gave it pitch black background because i have my terminals all pitch black, and have stylished several websites including google to pitch black & i disliked the grey background instead of #000000)

(bright light can give me migraines, that FFFFFF background had to go)

(script syntax has been hijacked from linux from scratch manuals)

bottom link of this thread is a style i submited to turn ubuntu forums black using stylish.  give er a whirl in firefox and sea monkey so ubuntu forums is not punishing your eyes either.

[http://ubuntuforums.org/showthread.php?t=1759760](http://ubuntuforums.org/showthread.php?t=1759760)

---

### Post by spas87 on 2011-09-17
does anyone have the script used in Linux Mint 9 i loved they're colours especially the lime green :_).

---

### Post by boblizar on 2011-09-21
tell you what, since my friend advocates linux mint, ill make a virtual machine and make its color formats cross over to ubuntu.

after the install i find the gedit to be exactly the same as ubuntus starting out.....  no lime green text?

[http://www.mkoby.com/2010/02/13/gedit-color-themes/](http://www.mkoby.com/2010/02/13/gedit-color-themes/)

take the XML files from the [repository]("http://github.com/mig/gedit-themes")

gedit them into a file in your desktop or downloads folder

then....

alt + f2

gedit

run

then.......

edit > preferences > font & colors


then hit the "add" button and search for the XML gedit font / color file you just created using the repository/external style source......

installing a font/color this way will leave the font/color removable from gedit as a user.....

the script from my first post on this thread will make it so only root can remove that theme......

---

### Post by lunatico on 2012-11-06
> **boblizar said:**
> 
then close the dialog, and then go to tools > highlight misspelled words

&& bug in new gedit found wont keep settings to highlight misspelled words

Hi,

Do you know if there is a way to make gedit have the highlight misspelled words options always on?

Thanks!

---

### Post by wildmanne39 on 2012-11-06
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

