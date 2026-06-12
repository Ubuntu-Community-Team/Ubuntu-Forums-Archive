---
title: "Unable to install critical Libpng12-0 dependency"
date: 2019-12-06
forum: Installation &amp; Upgrades
---

### Post by penguin-fach on 2019-12-06
A significant number of major software vendors are still releasing Linux software requiring Libpng12-0 as a dependency. I have tried a number of methods to get this library to install correctly in Kubuntu 19.10 and vanilla Ubuntu 18.04 LTS but with no success. As recommended I have used the Ubuntu .deb library from the Xenial repository and tried several packages to install it but get the same libpng12.so.0 file not found error reported by others. The most progress I made was using Synpatic but with the same outcome - file not found.

I don't know enough about the structure of the library to determine whether there is critical information missing in the Ubuntu library or changes in the way Ubuntu handles libraries may be to blame. It is also possible that the issue lies with inadequate installation resolution between 32 and 64 bit architectures.

I have critical technical software that is supposed to be compatible with 18.04 LTS but clearly isn't and the vendor, Picotech, is unresponsive. Some users have managed to install the application successfully but it looks like this has been on upgraded machines that have retained Libpng12-0 due to other dependencies.

This Libpng12-0 issue is an ongoing problem for a lot of people and I really need to get this sorted. Can anyone shed additional light on this?

---

### Post by Frogs Hair on 2019-12-06
I downloaded picoLog6 from Pico Tech  just to test and received a functioning app image. Is the software you are using an appimage? I ask because appimages generally have self contained dependencies. I'm using the Ubuntu development version with libpng16-16 however, I don't think this makes a difference due to the software being an appimage.

---

### Post by penguin-fach on 2019-12-07
> **Frogs Hair said:**
> I downloaded picoLog6 from Pico Tech  just to test and received a functioning app image. Is the software you are using an appimage? I ask because appimages generally have self contained dependencies. I'm using the Ubuntu development version with libpng16-16 however, I don't think this makes a difference due to the software being an appimage.

Thanks for your response.

I had assumed that was what I had done but you have me wondering now. I downloaded as per the instructions on the Picotech webpage at [https://www.picotech.com/downloads/linux](https://www.picotech.com/downloads/linux) and can't see any other build options.

There is an appimage download page here [https://www.picotech.com/downloads/_lightbox/PicoScope6](https://www.picotech.com/downloads/_lightbox/PicoScope6) but I have been unable to find PicoScope 6 for Linux on that page. There are appimage downloads for PicoLog but that is not what I am after.

---

### Post by Frogs Hair on 2019-12-07
I get an error , but don't understand the cause other than I don't have the hardware.  


```
File: trace.xml
Path: /home/d-pc/.local/share/Pico Technology/260a68f1-c314-451b-830f-0a5e01d65514/trace.xml
Contents: 
<?xml version="1.0" encoding="utf-8" standalone="yes"?><document>
    <event time="07/12/19 08:57:17.058" level="Info">Trace opened 12/7/2019.</event>
    <event time="07/12/19 08:57:17.152" category="ApplicationInfo" level="Info">Application 'PicoScope 6 Beta' (version 6.13.7.707) starting.</event>
    <event time="07/12/19 08:57:17.173" category="ID" level="Info">962E7BC55CE7CCADC0701F4BFE75F434</event>
    <event time="07/12/19 08:57:17.176" category="Environment" level="Info">User is not Guest</event>
    <event time="07/12/19 08:57:17.177" category="Environment" level="Info">No Administrator Privileges</event>
    <event time="07/12/19 08:57:17.177" category="Environment" level="Info">Failed to detect access rights</event>
    <event time="07/12/19 08:57:17.178" category="Environment" level="Info">Host Operating System - Linux</event>
    <event time="07/12/19 08:57:17.178" category="Environment" level="Info">OS Version - Unix 5.3.0.18</event>
    <event time="07/12/19 08:57:17.178" category="Environment" level="Info">.net Version - 4.0.30319.42000</event>
    <event time="07/12/19 08:57:17.178" category="Environment" level="Info">Running on Mono - True</event>
    <event time="07/12/19 08:57:17.178" category="Environment" level="Info">Mono Display Name - 4.6.2 (Stable 4.6.2.16/ac9e222 Thu Apr 20 10:05:37 BST 2017)</event>
    <event time="07/12/19 08:57:17.179" category="Environment" level="Info">Current Directory - /opt/picoscope/lib</event>
    <event time="07/12/19 08:57:17.179" level="Info">Processor Count - 4</event>
    <event time="07/12/19 08:57:17.179" category="Environment" level="Info">64Bit Operating System - True</event>
    <event time="07/12/19 08:57:17.179" category="Environment" level="Info">64Bit Process - True</event>
    <event time="07/12/19 08:57:17.180" category="Environment" level="Info">Command Line - /opt/picoscope/lib/PicoScope.GTK.exe</event>
    <event time="07/12/19 08:57:17.180" category="ApplicationInfo" level="Info">Settings file version - 11.3.1</event>
    <event time="07/12/19 08:57:17.180" category="ApplicationInfo" level="Info">Preferences file version - 2.0.0</event>
    <event time="07/12/19 08:57:17.180" category="ApplicationInfo" level="Info">Probes file version - 1.0.0</event>
    <event time="07/12/19 08:57:17.181" category="ApplicationInfo" level="Info">Data file binary header version - 1</event>
    <event time="07/12/19 08:57:17.196" level="Error">Creating Preferences file.</event>
    <event time="07/12/19 08:57:17.310" level="Info">Using default culture: English (United States).</event>
    <event time="07/12/19 08:57:17.635" category="Exception" level="Error">Unhandled Exception 1:System.TypeInitializationException: The type initializer for 'System.Drawing.GDIPlus' threw an exception. ---&gt; System.DllNotFoundException: /opt/picomono/lib/libgdiplus.so
  at (wrapper managed-to-native) System.Drawing.GDIPlus:GdiplusStartup (ulong&amp;,System.Drawing.GdiplusStartupInput&amp;,System.Drawing.GdiplusStartupOutput&amp;)
  at System.Drawing.GDIPlus..cctor () [0x000cc] in &lt;1917aa1c39d94b1a91807b8cd9f03350&gt;:0 
   --- End of inner exception stack trace ---
  at System.Drawing.Icon.GetInternalBitmap () [0x0000b] in &lt;1917aa1c39d94b1a91807b8cd9f03350&gt;:0 
  at System.Drawing.Icon.ToBitmap () [0x0001b] in &lt;1917aa1c39d94b1a91807b8cd9f03350&gt;:0 
  at (wrapper remoting-invoke-with-check) System.Drawing.Icon:ToBitmap ()
  at Pico.&#57465;..ctor () [0x00097] in &lt;6b774d82131044baaefb7b6415580f0b&gt;:0 
  at Pico.&#57348;.&#57345; () [0x00044] in &lt;6b774d82131044baaefb7b6415580f0b&gt;:0 
  at Pico.&#57348;.RunApplication (System.Collections.Generic.List`1[T] startupErrors) [0x00037] in &lt;2ee687ea0fcb44359ca9fe09ef46e18c&gt;:0 
  at Pico.&#57348;.&#57344; () [0x00103] in &lt;6b774d82131044baaefb7b6415580f0b&gt;:0 
  at Pico.&#57348;.Main () [0x00040] in &lt;6b774d82131044baaefb7b6415580f0b&gt;:0 </event>
    <event time="07/12/19 08:57:17.636" category="Exception" level="Error">Inner Exception:System.DllNotFoundException: /opt/picomono/lib/libgdiplus.so
  at (wrapper managed-to-native) System.Drawing.GDIPlus:GdiplusStartup (ulong&amp;,System.Drawing.GdiplusStartupInput&amp;,System.Drawing.GdiplusStartupOutput&amp;)
  at System.Drawing.GDIPlus..cctor () [0x000cc] in &lt;1917aa1c39d94b1a91807b8cd9f03350&gt;:0 </event>
    <event time="07/12/19 08:57:18.640">Trace Closing</event>
</document>

```

---

### Post by penguin-fach on 2019-12-08
Following up on your trace data I found another post referencing a similar problem in OpenSUSE which suggested installing libgdiplus. I tried this on two Ubuntu builds, Ubuntu 18.04 LTS and Kubuntu 19.10. It worked in both cases. I am not at work so I can't try and live instrument but the core application is working.

I would be interested to know if this works for you too.

---

### Post by Frogs Hair on 2019-12-08
That was it ! I selected demo because I have no hardware.

---

### Post by penguin-fach on 2019-12-08
Brilliant! Finding that it is riddled with bugs but, hey, this is a start.

Thanks for your help.

---

