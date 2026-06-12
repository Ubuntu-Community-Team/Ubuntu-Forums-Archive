---
title: "grub menu"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by camstar on 2010-01-24
Have a triple boot system (Karmic,XP & win7) All is working well but I want to change the grub menu item that shows :
 "Window 7 (loader)" and I would like to change this to :Windows Systems"
I followed all the instructions in the "Grub 2 Title Tweaks #1 

3. Copy the exact title you wish to change (Example: Microsoft Windows XP Home Edition ) and place it between the quotes in the first line below.
4. Enter the desired title between the quotes in the second line below - in this example, "Windows XP" would replace "Enter Desired New Title Here".
Code:
# Original
# if [ -z "${LONGNAME}" ] ; then
#    LONGNAME="${LABEL}"
# fi

  if [ "${LONGNAME}" = ["Window 7 (loader)" ] ; then
    LONGNAME="Windows Systems"
  elif [ -z "${LONGNAME}" ] ; then
    LONGNAME="${LABEL}"
  fi

After doing this and running update-grub it still keeps giving me an "unexpected operator" error
Tried to change it several times but no luck.
Any help will be appreciated

SP

---

### Post by meierfra. on 2010-01-24
> 
if [ "${LONGNAME}" = [COLOR="Red"][[/COLOR]"Window 7 (loader)" ] ; then
LONGNAME="Windows Systems"
elif [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi



Remove the "[" in the middle of the first line, so it looks like

```
if [ "${LONGNAME}" =  "Window 7 (loader)" ]
```

---

### Post by camstar on 2010-01-26
thanks. that worked.

---

