---
title: "[SOLVED] MonoDevelop fails to start"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by kweinert on 2008-04-26
I did the update via the net.

Now I have a small problem when I try to start MonoDevelop. Actually 2 of them, but one is easy to fix.

The first is that libgtkembedmoz.so isn't found - fixable by setting MOZILLA_FIVE_HOME to /usr/lib/thunderbird. I'm just not sure why it should require manual intervention.

The more important and difficult problem is this error that I get:

[FONT="Fixedsys"]System.TypeInitializationException: An exception was thrown by the type initializer for MonoDevelop.Core.Gui.Services ---> System.InvalidOperationException: Extension node not found in path: /MonoDevelop/Core/PlatformService
  at Mono.Addins.ExtensionContext.GetExtensionObjects (System.String path, System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
  at Mono.Addins.ExtensionContext.GetExtensionObjects (System.String path) [0x00000] 
  at Mono.Addins.AddinManager.GetExtensionObjects (System.String path) [0x00000] 
  at MonoDevelop.Core.Gui.Services..cctor () [0x00000] --- End of inner exception stack trace ---

  at MonoDevelop.Ide.Gui.IdeApp.Initialize (IProgressMonitor monitor) [0x00000] 
  at MonoDevelop.Ide.Gui.IdeStartup.Run (System.String[] args) [0x00000] 

[/FONT]

I believe that I've installed everything Mono that's available at this point in time to no avail.

Anyone have any hints/tips/pointers/RTFMs?

Thanks.

---

### Post by herorev on 2008-05-11
I'm also getting this exception on startup, on Ubuntu 8.04 64-bit, upgraded from Ubuntu 7.10 64-bit.

---

### Post by kweinert on 2008-05-11
A quick update.

I can tell you what I found, and what fixed the problem.

Because MonoDevelop was so "down-version" on Ubuntu, at some point in the past I had done a manual install into /usr/local.

Of course, by the time I upgraded and reinstalled MonoDevelop, I had forgotten that.

My first clue was when I completely uninstalled (through synaptic) Mono and MonoDevelop, but gacutil still told me I had things installed (like the down version of gtksharp) and I got to looking around.

After I removed all the mono/monodevelop elements from /usr/local and then did a reinstall of them from synaptic the problem "miraculously" fixed itself :)

It does explain why it was an edge case in the upgrades - it's hard to account for cranial-rectal inversion in an installer. :)

Good luck hunting your problem down.

---

### Post by herorev on 2008-05-11
After multiple unsuccessful trials of:
[LIST]
[*]uninstalling every package related to mono
[*]deleting files related to mono
[*]reinstalling the mono packages
[/LIST]
I eventually just decided to do a search from the root directory and delete every single file related to mono I could find.

I think deleting /opt/mono-1.9 did the trick. It turns out the mono packages in Ubuntu's repository don't create such a directory, so this directory was probably created from me building Mono from source.

MonoDevelop is now starting up successfully.

(However, I've still got problems. Calling the Load method of XmlDocument objects gives me a segmentation fault. *sigh* Why is Mono so full of bugs?)

---

