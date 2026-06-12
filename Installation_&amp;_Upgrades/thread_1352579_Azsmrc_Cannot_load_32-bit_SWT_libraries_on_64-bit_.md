---
title: "Azsmrc: Cannot load 32-bit SWT libraries on 64-bit JV"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Zilioum on 2009-12-11
I use the Azsmrc Remote control tool on my notebook to control my download server. I now want to use Azsmrc on my new Desktop that runs jaunty 64bit. I copied the Azsmrc folder from my notebook to the desktop, ran the script and got the following error. 

```
java.lang.UnsatisfiedLinkError: Cannot load 32-bit SWT libraries on 64-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:177)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
	at org.eclipse.swt.internal.C.<clinit>(C.java:21)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:130)
	at lbms.azsmrc.remote.client.swtgui.RCMain.init(RCMain.java:619)
	at lbms.azsmrc.remote.client.swtgui.RCMain.start(RCMain.java:168)
	at lbms.azsmrc.remote.client.swtgui.Starter.launch(Starter.java:22)
	at lbms.tools.launcher.Launcher.main(Launcher.java:63)

```

I did install Java and I also tried to solve the problem by installing the swt packages, nothing worked. Any suggestions?

---

### Post by Zilioum on 2009-12-11
I was able to solve the problem on my own. Here's how I did it:

It turns out that the swt.jar that was still in my Azsmrc folder, was not compatible with my 64-bit Ubuntu. 

I downloaded the appropriate SWT library from: [http://download.eclipse.org/eclipse/downloads/drops/R-3.5.1-200909170800/index.php#SWT]("http://download.eclipse.org/eclipse/downloads/drops/R-3.5.1-200909170800/index.php#SWT")
*(I didn't find a better link: Scroll down to "SWT Binary and Sources" and choose the 64-bit version)*

I then extracted _all_ the files from the zip into my Azsmrc folder, thus replacing the old/wrong SWT.

Azsmrc now works perfectly.

Feel free to ask if you need some help.

Cheers

---

### Post by FOSman on 2009-12-11
I've never used Azsmrc or run Azureus on a 64-bit system, so don't take my advice as gospel.  That said, it appears you're problem is noted right in the error message.
> Cannot load 32-bit SWT libraries on 64-bit JVM
You need to get the 64-bit SWT libraries.  Google should be able to find them for you.  Swap them out and you should be good.  If not, I'd suggest posting to the Azureus/Vuze forums.  They're probably far more likely to be able to help you out.  [http://forum.vuze.com/](http://forum.vuze.com/)

---

### Post by Zilioum on 2009-12-11
That's exactly what I did :D 

Thanks anyway!

---

