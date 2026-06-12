---
title: "Wine Failing at Everything"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by crisnoh on 2010-03-21
Been having some issues getting wine to install various programs.  Here's the terminal output for the most recent:

```
$ wine Evernote_3.5.2.1764.exe 
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  85
  Current serial number in output stream:  85
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  85
  Current serial number in output stream:  85
```

I can't even open wine's configuration window or notepad, which is installed by default.

Is anybody able to point me in the direction of a fix for this?

---

### Post by asmoore82 on 2010-03-22
I never had a problem with Ubuntu 9.04 and below, but I've also never been able to use Compiz.

Now I've been running Ubuntu 10.04 since Alpha 2 and loving it, Compiz works out-of-the-box too.
But I've been getting this and similar wine errors off and on.

You could try setting this wine registry value:
HKEY_CURRENT_USER\Software\Wine\X11 Driver\UseXVidMode = "N"

But of course you can't open the wine registry editor if wine can't launch,
so this will set the same value:
```
cat >>"$HOME/.wine/user.reg" <<EOF

[Software\\\\Wine\\\\X11 Driver] 1269299093
"UseXVidMode"="N"
EOF
```

When Wine is working, you can open the registry editor with
```
wine regedit
```

---

### Post by crisnoh on 2010-03-28
Sorry, should have gotten in here to update.  Most recent Wine update cleared up the problem.

---

