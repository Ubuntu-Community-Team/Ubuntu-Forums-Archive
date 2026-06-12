---
title: "MonoDevelop doesn't work after update"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by bwilhiteforex on 2008-11-03
I'm running Xubuntu 8.04...

I just did "sudo apt-get update"
and "sudo apt-get upgrade"

...and now my installation of MonoDevelop doesn't work.  I've uninstalled and re-installed it and it still doesn't work.  So I tried to start it from the terminal, and it gave me this error:

"Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for MonoDevelop.Core.PropertyService ---> System.Xml.XmlException: Document element did not appear. file:///home/brandon/.config/MonoDevelop/MonoDevelopProperties.xml Line 1, position 1.
  at Mono.Xml2.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlTextReader.Read () [0x00000] 
  at MonoDevelop.Core.Properties.Load (System.String fileName) [0x00000] 
  at MonoDevelop.Core.PropertyService.LoadProperties (System.String fileName) [0x00000] 
  at MonoDevelop.Core.PropertyService..cctor () [0x00000] --- End of inner exception stack trace ---

  at MonoDevelop.Core.Runtime.Initialize (Boolean updateAddinRegistry) [0x00000] 
  at MonoDevelop.Startup.SharpDevelopMain.Main (System.String[] args) [0x00000]"

So I looked at the xml document referenced, and it's empty!

I'm not sure where to go from here.  Any ideas?

---

### Post by bwilhiteforex on 2008-11-03
Ok. 

I just did:

"sudo apt-get purge monodevelop"
then I deleted the config directory referenced in the exception,
and then I re-installed monodevelop

Then I restarted monodevelop from the applications menu, and it re-created the directory and the files for me.  It all works fine now.

---

