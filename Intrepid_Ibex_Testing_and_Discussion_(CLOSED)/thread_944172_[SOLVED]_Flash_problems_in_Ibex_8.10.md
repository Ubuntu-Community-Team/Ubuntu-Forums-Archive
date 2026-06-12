---
title: "[SOLVED] Flash problems in Ibex 8.10"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alienexplorers on 2008-10-11
When I try to run a flash movie or animation firefox 3.0.3 crashes.  I am running Flash 10rc which I believe is the newest version.  I don't know if a problem report has been submitted or if I should submit one.  I just am not sure what to post in the error report since I do not get an error message.  Any help you could supply like telling me if the error report should be sent to Adobe or the Launchpad.

---

### Post by Kow on 2008-10-11
Try running firefox from the command-line (Applications->Accessories->Terminal, "firefox www.google.com") and report back any messages that occur when you go to one of the sites that uses flash and causes a crash. Just a little forewarning, if the issue is narrowed down to the adobe flash plug-in then there is not much that can be done. I can say out of personal experience that random crashes from the nonfree (adobe) flash plugin are almost normal, consistent crashes not so much.

---

### Post by alienexplorers on 2008-10-11
Tried running firefox from terminal and went to youtube and it crashed.  No data came up in terminal, just my terminal name and thats all.  This is driving me nuts.  Just one error message is all I am looking for.

---

### Post by Kow on 2008-10-11
Try a different version of flash. If that resolves the issue then it is in all likelihood a flash bug. If the problem persists then it is likely not a flash bug.

---

### Post by taavikko on 2008-10-11
Close all existing FF instances, then

```
firefox www.youtube.com > ~/flash-crash.log 2>&1
```
Does that print out anything, I had a bunch of Icedtea entries.

---

### Post by alienexplorers on 2008-10-11
Here is the output of flash-crash.log:
```
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object HTMLDocument])
## ##  mpc_extractStreamInternal2 1ms
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object HTMLDocument])
## ##  mpc_extractStreamInternal2 1ms
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## ##  mpc_extractStreamInternal2 2ms
#  pageshow
## mpc_extractStreamOnDoc (chrome://browser/content/browser.xul)
## mpc_extractStreamInternal2 (undefined, [object XULDocument])
## ##  mpc_extractStreamInternal2 3ms
#  pageshow
## mpc_extractStreamOnDoc (http://monopoly.promotions.com/monopoly08/)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## ##  mpc_extractStreamInternal2 1ms
#  pageshow
## mpc_extractStreamOnDoc (chrome://browser/content/bookmarks/bookmarksPanel.xul)
## mpc_extractStreamInternal2 (undefined, [object XULDocument])
## ##  mpc_extractStreamInternal2 1ms
## mpc_isSideBarOpen()
## window.defaultStatus =
window.menubar =[object BarProp]
window.menubar.visible  =true
window.navigator  =[object Navigator]
window.scrollbars  =[object BarProp]
window.status  =
## mpc_canOpenSideBar()
## mpc_isSideBarOpen()
## window.defaultStatus =
window.menubar =[object BarProp]
window.menubar.visible  =true
window.navigator  =[object Navigator]
window.scrollbars  =[object BarProp]
window.status  =
## mpc_canOpenSideBar()
## mpc_extractStreamInternal (http://monopoly.promotions.com/monopoly08/, [object XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu (http://i.promotions.com/monopoly08/flash/Main.swf,http://i.promotions.com/monopoly08/flash/Main.swf,application/x-shockwave-flash,http://monopoly.promotions.com/monopoly08/front.do)
## mpc_IntermediateEmbedMediaFile(http://i.promotions.com/monopoly08/flash/Main.swf)
## ##  mpc_extractStreamInternal2 506ms
#  pageshow
## mpc_extractStreamOnDoc (http://monopoly.promotions.com/monopoly08/front.do)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu (http://i.promotions.com/monopoly08/flash/Main.swf,http://i.promotions.com/monopoly08/flash/Main.swf,application/x-shockwave-flash,http://monopoly.promotions.com/monopoly08/front.do)
## mpc_IntermediateEmbedMediaFile(http://i.promotions.com/monopoly08/flash/Main.swf)
## ##  mpc_extractStreamInternal2 4ms
#  pageshow
## mpc_extractStreamOnDoc (about:blank)
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal (http://monopoly.promotions.com/monopoly08/front.do, [object XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal (http://monopoly.promotions.com/monopoly08/front.do, [object XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu (http://i.promotions.com/monopoly08/flash/Main.swf,http://i.promotions.com/monopoly08/flash/Main.swf,application/x-shockwave-flash,http://monopoly.promotions.com/monopoly08/front.do)
## mpc_IntermediateEmbedMediaFile(http://i.promotions.com/monopoly08/flash/Main.swf)
## ##  mpc_extractStreamInternal2 5ms
## mpc_extractStreamInternal (about:blank, [object XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal (about:blank, [object XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu (http://i.promotions.com/monopoly08/flash/Main.swf,http://i.promotions.com/monopoly08/flash/Main.swf,application/x-shockwave-flash,http://monopoly.promotions.com/monopoly08/front.do)
## mpc_IntermediateEmbedMediaFile(http://i.promotions.com/monopoly08/flash/Main.swf)
## ##  mpc_extractStreamInternal2 7ms
## mpc_extractStreamInternal (about:document-onload-blocker, [object XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal (about:document-onload-blocker, [object XPCNativeWrapper [object Window]])
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## ##  mpc_extractStreamInternal2 1ms
## mpc_extractStreamInternal2 (undefined, [object XPCNativeWrapper [object HTMLDocument]])
## mpc_getMimeTypeForNode([object XPCNativeWrapper [object HTMLEmbedElement]])
## mpc_getSourceMediaOfNode([object XPCNativeWrapper [object HTMLEmbedElement]])   name=embed
## mpc_addInfoForContextMenuAndFloatingMenu (http://i.promotions.com/monopoly08/flash/Main.swf,http://i.promotions.com/monopoly08/flash/Main.swf,application/x-shockwave-flash,http://monopoly.promotions.com/monopoly08/front.do)
## mpc_IntermediateEmbedMediaFile(http://i.promotions.com/monopoly08/flash/Main.swf)
## ##  mpc_extractStreamInternal2 5ms
```
When the program crashed I got a message in the Terminal stating illegal Instruction.

---

### Post by Lorenz on 2008-10-11
Flash doesn't work at all for me anymore, can anyone point me into the right direction? It claims the plugin is installed, but when i surf to youtube for example it says I don't have flash installed. thanks!

---

### Post by elj4176 on 2008-10-11
I just removed and re-installed the flashplugin-nonfree and it worked after that.

---

