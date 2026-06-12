---
title: "Installing iTunes"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by orozcovision on 2007-06-29
Hello Everyone,

I just upgraded wine to version 0.9.39 and was finally able to install Macromedia Flash 8. Since I was having a pretty good day... I thought I'd try to install some other software.

I'm sure everyone here knows, Apple is launching their new iPhone tomorrow, 6/29/07. It's designed to work with iTunes, so I figured iTunes would be something many would like to have.

1). I downloaded the iTunesSetup.exe for Windows from [http://www.apple.com](http://www.apple.com).
2). Installed iTunes by typing the following at my Command Prompt: sudo wine "C:\iTunesSetup.exe"

The install prompted to install Quicktime 7, and that installed just fine.  After iTunes successfully installed, I tried launching the application by typing the following in a command prompt:

wine "C:\Program Files\iTunes\iTunes.exe"

I Originally received errors about the Sound Driver being set to Hardware.  I ran "winecfg" and set the Audio for "OSS", and also set it for "Emulation"

Ran the following at the command prompt again:

wine "C:\Program Files\iTunes\iTunes.exe"

Received quite a few Errors again, but could not figure them out.  See below:

//----------------------------------------------------
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1a8ef8) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1877f0)->((nil),00000008)
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\QTFont.for","c:\\windows\\QTFont.qfn",(null)): stub
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33eea0
fixme:wintrust:WTHelperProvDataFromStateData (nil)
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33eea0
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1877f0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
-------------------------------------------------------//

Any Help in getting this app running is greatly appreciated! Thanks in Advance.

--
OrozcoVision

---

### Post by orozcovision on 2007-06-29
Found more info here: [http://appdb.winehq.org/appview.php?iVersionId=5774](http://appdb.winehq.org/appview.php?iVersionId=5774)

Hope that helps somewhat.

--
OrozcoVision

---

### Post by macmatt on 2007-06-29
hmmm :)

---

### Post by justin whitaker on 2007-06-29
The 4 series runs on Crossover Office, but nothing from iTunes 6 on runs on Wine yet.

---

### Post by orozcovision on 2007-06-29
After carefully re-reading the errors, and with some help from the posted link above... it seems that iTunes requires two dlls.

1). crypt32.dll
2). wintrust.dll

I grabbed these two dlls from an iTunes install on Windows XP. Copied them over to Wine's /system32 directory.

Tried launching iTunes again, but errors indicated that it was also dependant of another dll

1). msasn1.dll.

Grabbed that dll and copied it over from the XP install to Wine's /system32.

Now when trying to run iTunes, I get the following:

Screen turns black until I grab the Command Prompt's handle. Then errors continue:

//---------------------------------------------------
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1a9d28) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1990c0)->((nil),00000008)
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\QTFont.for","c:\\windows\\QTFont.qfn",(null)): stub
fixme:sync:RegisterWaitForSingleObject 0x77b054f8 0x64 0x77afa0da (nil) -1 4
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1990c0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
----------------------------------------------------//

---

### Post by orozcovision on 2007-06-29
> **justin whitaker said:**
> The 4 series runs on Crossover Office, but nothing from iTunes 6 on runs on Wine yet.

Thanks for your Reply Justin. However, the iPhone will only work with 7+ series.

--
OrozcoVision

---

### Post by orozcovision on 2007-06-29
NOTE: I added Crypt32.dll and Wintrust.dll as override libaries in winecfg. (Set to Native windows).

---

### Post by orozcovision on 2007-06-29
The Error: "fixme:rpc:NdrClientCall2 new correlation description not implemented" corresponds to the rpcrt4.dll.  

1). grabbed this dll from the XP install.
2). Copied it over the wine's /system32
3). Successfully Registered the dll using "wine regsvr32 rpcrt4.dll" NOTE: I had to navigate to wine's system32 dir in order for regsvr32 to find the dll.

I now get the following errors relating to ntdll.dll.  I followed the same steps above for ntdll.dll, but continued to get these same errors.

//--------------------------------------------------------------------
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:ntdll:NtCreatePort (0x178710,0x33f4bc,188,256,(nil)),stub!
err:ole:RPC_StartRemoting Couldn't register endpoint L"\\pipe\\OLE_0000000800000009"
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x19b520) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x18ac18)->((nil),00000008)
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\QTFont.for","c:\\windows\\QTFont.qfn",(null)): stub
fixme:sync:RegisterWaitForSingleObject 0x77b054f8 0x64 0x77afa0da (nil) -1 4
fixme:ntdll:NtConnectPort (0x217b28,L"\\RPC Control\\keysvc",0x33e2a4,(nil),(nil),(nil),0x33e2cc,0x33e2b4),stub!
fixme:ntdll:NtConnectPort (0x217b28,L"\\RPC Control\\keysvc",0x33e2a4,(nil),(nil),(nil),0x33e2cc,0x33e2b4),stub!
fixme:ntdll:NtConnectPort (0x217b28,L"\\RPC Control\\keysvc",0x33e2a4,(nil),(nil),(nil),0x33e2cc,0x33e2b4),stub!
fixme:ntdll:NtConnectPort (0x377dfd0,L"\\RPC Control\\keysvc",0x33e25c,(nil),(nil),(nil),0x33e284,0x33e26c),stub!
fixme:ntdll:NtConnectPort (0x377dfd0,L"\\RPC Control\\keysvc",0x33e25c,(nil),(nil),(nil),0x33e284,0x33e26c),stub!
fixme:ntdll:NtConnectPort (0x377dfd0,L"\\RPC Control\\keysvc",0x33e25c,(nil),(nil),(nil),0x33e284,0x33e26c),stub!
fixme:ntdll:NtConnectPort (0x217cc8,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217cc8,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217cc8,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217b38,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x217b38,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x217b38,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x217a48,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217a48,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217a48,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217d10,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x217d10,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x217d10,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x217d10,L"\\RPC Control\\keysvc",0x33e2a4,(nil),(nil),(nil),0x33e2cc,0x33e2b4),stub!
fixme:ntdll:NtConnectPort (0x217d10,L"\\RPC Control\\keysvc",0x33e2a4,(nil),(nil),(nil),0x33e2cc,0x33e2b4),stub!
fixme:ntdll:NtConnectPort (0x217d10,L"\\RPC Control\\keysvc",0x33e2a4,(nil),(nil),(nil),0x33e2cc,0x33e2b4),stub!
fixme:ntdll:NtConnectPort (0x217e00,L"\\RPC Control\\keysvc",0x33e25c,(nil),(nil),(nil),0x33e284,0x33e26c),stub!
fixme:ntdll:NtConnectPort (0x217e00,L"\\RPC Control\\keysvc",0x33e25c,(nil),(nil),(nil),0x33e284,0x33e26c),stub!
fixme:ntdll:NtConnectPort (0x217e00,L"\\RPC Control\\keysvc",0x33e25c,(nil),(nil),(nil),0x33e284,0x33e26c),stub!
fixme:ntdll:NtConnectPort (0x217e00,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217e00,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217e00,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x377e170,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x377e170,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x377e170,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x377dfd0,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x377dfd0,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x377dfd0,L"\\RPC Control\\keysvc",0x33e278,(nil),(nil),(nil),0x33e2a0,0x33e288),stub!
fixme:ntdll:NtConnectPort (0x217e68,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x217e68,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ntdll:NtConnectPort (0x217e68,L"\\RPC Control\\keysvc",0x33e230,(nil),(nil),(nil),0x33e258,0x33e240),stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x18ac18)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
-----------------------------------------------------------------//

Has anyone ever seen this error?

--
OrozcoVision

---

### Post by justin whitaker on 2007-06-29
Does Wine implement RPC?

---

### Post by orozcovision on 2007-06-29
Yes. You can override it to native/or builtin using "winecfg>Libraries"

---

### Post by justin whitaker on 2007-06-29
> **orozcovision said:**
> Yes. You can override it to native/or builtin using "winecfg>Libraries"

That is good to know. Thanks!

---

### Post by orozcovision on 2007-06-29
Fixed the following error :

//--------------------------------------
err:ole:RPC_StartRemoting Couldn't register endpoint L"\\pipe\\OLE_0000000800000009"
------------------------------------//

and got RPC working after copying over all "ole*.dll" files from my XP install into wine's /system32 dir.  I registered ole32.dll & oleaut32.dll. Set both to native in winecfg.

Hope that helps.

--
OrozcoVision

---

### Post by orozcovision on 2007-06-29
So it's 5pm PST, just an hour before Apple opens it's doors for the iPhone.  Has anyone had any luck getting past errors? If so, can you please post your steps so we can also try? Thanks in advance

Best,
OrozcoVision

---

### Post by macmatt on 2007-07-27
Here - I think I have the solution...


__G__E__T______A______M___A___C___!___!__

Problem solved.

---

### Post by ballygowanboy on 2007-07-27
i too would like to install itunes, is there a straight forward way to do this?

---

### Post by mikewhatever on 2007-07-27
Nice as ipod is, this thread makes me glad I don't have one. My iaudio needs no software and is detected by Ubuntu every time it is plugged in. I truly hope one day you guys can use iTunes. Good luck with your efforts.

---

