---
title: "wine programm requires mono for windows"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by scott36 on 2011-02-08
Hello everybody,

I am trying to install a program named "Ntrip" with wine, running Linux Mint 10 64bit (based on Ubuntu 10.04)

I installed the software without problems, when I try to start it I get the following error:

```

fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
wine: Install the Windows version of Mono to run .NET executables

```As far as I know, mono is by default on every Ubuntu 10.04 installation, however as per the error message, I installed the Windows version of Mono via Wine successfully.

Trying to start the program again, still coming up with above error.

Any idea which version of Mono I need or what the problem there is?

Thank you for every help.

Scotty


(sorry, I have just seen that there is a Wine forum ;)

---

### Post by dino99 on 2011-02-08
try to install .NET with winetricks

---

### Post by scott36 on 2011-02-08
Thank you for that.

I installed the .net 2 framework now.

The application starts, but with plenty of errors. And I can not access the GPS tracker via USB.

Would anybody know about these errors:

```

fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:sync:CreateMemoryResourceNotification (0) stub
err:ole:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.resources"
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:shell:URL_ParseUrl failed to parse L"XPTable"
fixme:shell:URL_ParseUrl failed to parse L"RibbonMenuButtonControl"
fixme:shell:URL_ParseUrl failed to parse L"ZedGraph"
fixme:shell:URL_ParseUrl failed to parse L"Infralution.Localization"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms.resources"
fixme:shell:URL_ParseUrl failed to parse L"ZedGraph.resources"
fixme:shell:URL_ParseUrl failed to parse L"ZedGraph.resources"
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:shdocvw:WebBrowser_QueryInterface (0x1fa7b8)->({c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4} 0x32d328) interface not supported
fixme:shdocvw:ProvideClassInfo_GetClassInfo (0x1fa7b8)->(0x32d200)
fixme:shdocvw:WebBrowser_QueryInterface (0x1fa7b8)->({00000003-0000-0000-c000-000000000046} 0x32d19c) interface not supported
fixme:shdocvw:WebBrowser_QueryInterface (0x1fa7b8)->({00000144-0000-0000-c000-000000000046} 0x32d214) interface not supported
fixme:shdocvw:WebBrowser_get_LocationURL (0x1fa7b8)->(0x32dbc0)
fixme:shdocvw:WebBrowser_Refresh (0x1fa7b8)
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Data"
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:gdiplus:GdipCreateHalftonePalette stub
fixme:gdiplus:GdipGetNearestColor (0x3f2fed8, 0x32e55c): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x3f2fed8, 0x32e55c): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x3f2fed8, 0x32e55c): Passing color unmodified
fixme:gdiplus:GdipGetNearestColor (0x3f2fed8, 0x32e55c): Passing color unmodified
fixme:gdiplus:GdipTranslateLineTransform stub: 0x3f33bc8 1147.000000 59.000000 0
fixme:gdiplus:GdipTranslateLineTransform stub: 0x3f38ac0 1147.000000 824.000000 0
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32e868:3; TargetFrameName 0x32e840:0)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32baf4
fixme:iphlpapi:NotifyAddrChange (Handle 0x6fae8d8, overlapped 0x6fae8e0): stub
0[1dd1e0]: IMM32: InitKeyboardLayout, aKeyboardLayout=04070407, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1fa860)->((null) 1 0x32c22c (nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x1fa860)->(0x32c1fc)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
fixme:mshtml:nsChannel_Open (0x6d4e2f8)->(0x328560)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x6d4e8f0)->(0x32ae6c 0x32ae58 0)
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Thu, 07-Feb-2013 17:01:02 GMT; path=/; domain=.google.com")
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x73416a8)->(0x32ae6c 0x32ae58 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:jscript:Object_hasOwnProperty 
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x738bb10)->(0x32ae6c 0x32ae58 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x7512df8)->(0x32ae6c 0x32ae58 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4}
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {b196b283-bab4-101a-b69c-00aa00341d07}
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {00000144-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1fa860)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d0-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:shdocvw:ClientSite_GetContainer (0x1fa860)->(0x32e7a4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1fa860)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:WebBrowser_get_RegisterAsDropTarget (0x1fa7b8)->(0x32ce4c)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1fa7b8)->(0)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:ole:Context_CC_ContextCallback (0x1fa950/0x1fa954)->(0x79f277a5, 0x2aee4c8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x1fa950/0x1fa954)->(0x79f277a5, 0x2aee45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x1fa950/0x1fa954)->(0x79f277a5, 0x2aee45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\bob\\Lokale Einstellungen\\Anwendungsdaten\\NTRIP\\NTRIP.exe_Url_43fg2fduvotp5qyts5tl3swqj3xd3lnk\\1.2.9.2\\up9in748.newcfg" 1 536870916 (nil) (nil) 0xa54554 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\bob\\Lokale Einstellungen\\Anwendungsdaten\\NTRIP\\NTRIP.exe_Url_43fg2fduvotp5qyts5tl3swqj3xd3lnk\\1.2.9.2\\u1m2tiy3.newcfg" 1 536870916 (nil) (nil) 0xa95fa0 (nil)
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4}
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {b196b283-bab4-101a-b69c-00aa00341d07}
fixme:mshtml:CustomDoc_QueryInterface Unimplemented interface {00000144-0000-0000-c000-000000000046}
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32eda8:3; TargetFrameName 0x32ed80:0)
fixme:shell:URL_ParseUrl failed to parse L"System.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.resources"
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClientSite_GetContainer (0x1fa860)->(0x32ec34)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1fa860)->((null))
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1fa860)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
err:mshtml:nsChannelBSC_stop_binding RemoveRequest failed: 80004005
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 21
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:ole:Context_CC_ContextCallback (0x1fa950/0x1fa954)->(0x79f277a5, 0x2aee4c8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x1fa950/0x1fa954)->(0x79f277a5, 0x2aee45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x1fa950/0x1fa954)->(0x79f277a5, 0x2aee45c, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1fa7b8)
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1fa7b8)
fixme:gdiplus:GdipDrawImagePointsRect Color transforms not implemented
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1fa7b8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1fa7b8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1fa7b8)
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:comm:set_queue_size insize 8192 outsize 8192 unimplemented stub
fixme:shell:URL_ParseUrl failed to parse L"NTRIP.resources"
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\bob\\Lokale Einstellungen\\Anwendungsdaten\\NTRIP\\NTRIP.exe_Url_43fg2fduvotp5qyts5tl3swqj3xd3lnk\\1.2.9.2\\tnqa0kks.newcfg" 1 536870916 (nil) (nil) 0xa8aa20 (nil)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1fa7b8)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1b01d0)->((nil))

```Regards,

Scott

---

