---
title: "Grub 2 scripting - what's the recommended method?"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-07-29
i'm a bit unclear on what the 'proper' method for grub2 scripting is, it seems to involve adding custom entries to /etc/grub.d/ and then enabling disabling them with chmod -x, but this just seems to miss out on some of the new scripting joy of grub2
what i'm actually doing is creating the custom files i want and then commenting/uncommenting variables in a sort of custom header file to activate them (much like /etc/default/grub works)
as adding these custom variables to /etc/default/grub wont work as they arent exported by grub-mkconfig, i've added a line to that command to read in the custom header file and use those variables too, which seems a nicer way to me at any rate :) just wondered if there was a standard defined way of doing this or is it yet to be settled on?

/etc/grub.d/41_custom_header
```
#!/bin/bash
GRUB_HIDDEN_MENU=true
export GRUB_HIDDEN_MENU

```/etc/grub.d/42_hidden_menu
```
#!/bin/sh
if [ "${GRUB_HIDDEN_MENU}" = "true" ] ; then
 cat << EOF
if sleep --verbose --interruptible ${GRUB_TIMEOUT} ; then
 set timeout=0
else
 set timeout=-1
fi
EOF
fi

```/usr/sbin/grub-mkconfig
```
if test -f ${sysconfdir}/default/grub ; then
  . ${sysconfdir}/default/grub
fi

+if test -f ${sysconfdir}/grub.d/41_custom_header ; then
+  . ${sysconfdir}/grub.d/41_custom_header
+fi

# XXX: should this be deprecated at some point?
if [ "x${GRUB_TERMINAL}" != "x" ] ; then
  GRUB_TERMINAL_INPUT="${GRUB_TERMINAL}"
  GRUB_TERMINAL_OUTPUT="${GRUB_TERMINAL}"
fi

```

---

### Post by ranch hand on 2009-07-29
Beats me, check this thread.  It gets really interesting toward the end.

[http://ubuntuforums.org/showthread.php?t=1223280](http://ubuntuforums.org/showthread.php?t=1223280)

---

