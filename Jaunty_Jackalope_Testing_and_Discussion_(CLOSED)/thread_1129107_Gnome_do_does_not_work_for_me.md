---
title: "Gnome do does not work for me"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rocknrolf77 on 2009-04-18
I have a problem with gnome-do. Anyone who knows where the setting files are located. Maybe it helps to delete them.

When starting gnome-do from a terminal I get :

```
Stack overflow in unmanaged: IP: 0x506c20, fault addr: 0x7fff35796ff0
Stack overflow: IP: 0x506c20, fault addr: 0x7fff3578eff0
At Unmanaged
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Read (intptr,byte[],int,int,System.IO.MonoIOError&) <0x00054>
  at (wrapper managed-to-native) System.IO.MonoIO.Read (intptr,byte[],int,int,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream.ReadData (intptr,byte[],int,int) <0x0004f>
  at System.IO.FileStream.RefillBuffer () <0x00037>
  at System.IO.FileStream.ReadByte () <0x000e7>
  at Mono.Addins.Serialization.BinaryXmlReader.ReadNext () <0x00034>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00057>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00067>

```

---

### Post by Ericyzfr1 on 2009-04-18
The last time I installed it I did not have any issues with it in 9.04. On the other hand in 8.10, I had a version conflict where the system proposed an upgrade older than my installed version.

---

