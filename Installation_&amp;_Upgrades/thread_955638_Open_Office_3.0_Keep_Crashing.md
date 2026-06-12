---
title: "Open Office 3.0 Keep Crashing"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by kshsj777 on 2008-10-22
I following the tutorial here as far as the commands went: [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

But when I start OO, the splash screen comes up and the option to select what kind of document (text, spreadsheet etc.) to pick comes up, but then as soon as I click one, it crashes.

Here's the error report:

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE errormail:errormail PUBLIC "-//OpenOffice.org//DTD ErrorMail 1.0//EN" "errormail.dtd">
<errormail:errormail xmlns:errormail="http://openoffice.org/2002/errormail" usertype="">
<reportmail:mail xmlns:reportmail="http://openoffice.org/2002/reportmail" version="1.1" feedback="false" email="">
<reportmail:title></reportmail:title>
<reportmail:attachment name="description.txt" media-type="text/plain" class="UserComment"/>
<reportmail:attachment name="stack.txt" media-type="text/plain" class="pstack output"/>
</reportmail:mail>
<officeinfo:officeinfo xmlns:officeinfo="http://openoffice.org/2002/officeinfo" build="300m9(Build:9358)" platform="unxlngi6.pro" language="" exceptiontype="6" product="OpenOffice.org 3.0" procpath="/opt/openoffice.org3/program/"/>
<systeminfo:systeminfo xmlns:systeminfo="http://openoffice.org/2002/systeminfo">
<systeminfo:System name="Linux" version="#1 SMP Mon Aug 25 17:32:09 UTC 2008" build="2.6.24-21-generic" locale="en_US.UTF-8"/>
<systeminfo:CPU type="i686"/>
</systeminfo:systeminfo>
<errormail:Stack type="Linux">
<errormail:StackInfo pos="0" ip="0xb7e45c80" rel="0x1fc80" name="libuno_sal.so.3" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="1" ip="0xb7e46564" rel="0x20564" name="libuno_sal.so.3" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="2" ip="0xb7fe2420" rel="0x420" name="" ordinal="__kernel_sigreturn+0x0"/>
<errormail:StackInfo pos="3" ip="0xb7980a01" rel="0x2ca01" name="libc.so.6" path="/lib/tls/i686/cmov/" ordinal="abort+0x101"/>
<errormail:StackInfo pos="4" ip="0xb7b7aad1" rel="0xa8ad1" name="libstdc++.so.6" path="/opt/openoffice.org/ure/lib/" ordinal="_ZN9__gnu_cxx27__verbose_terminate_handlerEv+0x101"/>
<errormail:StackInfo pos="5" ip="0xb7b78505" rel="0xa6505" name="libstdc++.so.6" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="6" ip="0xb7b78542" rel="0xa6542" name="libstdc++.so.6" path="/opt/openoffice.org/ure/lib/"/>
<errormail:StackInfo pos="7" ip="0xb7b78739" rel="0xa6739" name="libstdc++.so.6" path="/opt/openoffice.org/ure/lib/" ordinal="__cxa_rethrow+0x59"/>
<errormail:StackInfo pos="8" ip="0xa8d47e90" rel="0x22e90" name="deploymentli.uno.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="9" ip="0xa8d4b9b3" rel="0x269b3" name="deploymentli.uno.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="10" ip="0xb670907f" rel="0xb507f" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic23ScriptExtensionIterator28implGetNextUserScriptPackageERb+0x1eb"/>
<errormail:StackInfo pos="11" ip="0xb6709428" rel="0xb5428" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic23ScriptExtensionIterator24nextBasicOrDialogLibraryERb+0x5c"/>
<errormail:StackInfo pos="12" ip="0xb670975a" rel="0xb575a" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic19SfxLibraryContainer18implScanExtensionsEv+0x27c"/>
<errormail:StackInfo pos="13" ip="0xb671523b" rel="0xc123b" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic19SfxLibraryContainer9init_ImplERKN3rtl8OUStringERKN3com3sun4star3uno9ReferenceINS7_5embed8XStorageEEE+0x25b7"/>
<errormail:StackInfo pos="14" ip="0xb67184a8" rel="0xc44a8" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic19SfxLibraryContainer4initERKN3rtl8OUStringERKN3com3sun4star3uno9ReferenceINS7_5embed8XStorageEEE+0x2a"/>
<errormail:StackInfo pos="15" ip="0xb671d507" rel="0xc9507" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic25SfxScriptLibraryContainerC1ERKN3com3sun4star3uno9ReferenceINS3_5embed8XStorageEEE+0x153"/>
<errormail:StackInfo pos="16" ip="0xb66c9449" rel="0x75449" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic14ImplRepository34impl_createApplicationBasicManagerEv+0x6c1"/>
<errormail:StackInfo pos="17" ip="0xb66c991d" rel="0x7591d" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic14ImplRepository26getApplicationBasicManagerEb+0x45"/>
<errormail:StackInfo pos="18" ip="0xb66ca647" rel="0x76647" name="libsbli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN5basic22BasicManagerRepository26getApplicationBasicManagerEb+0x1f"/>
<errormail:StackInfo pos="19" ip="0xb74503b4" rel="0x933b4" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN14SfxApplication15GetBasicManagerEv+0x2a"/>
<errormail:StackInfo pos="20" ip="0xb745034f" rel="0x9334f" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN14SfxApplication8GetBasicEv+0x19"/>
<errormail:StackInfo pos="21" ip="0xb7450384" rel="0x93384" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN14SfxApplication14EnterBasicCallEv+0x28"/>
<errormail:StackInfo pos="22" ip="0xb74503ac" rel="0x933ac" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN14SfxApplication15GetBasicManagerEv+0x22"/>
<errormail:StackInfo pos="23" ip="0xb74f9a9c" rel="0x13ca9c" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN14SfxObjectShell19SetCurrentComponentERKN3com3sun4star3uno9ReferenceINS3_10XInterfaceEEE+0x8c"/>
<errormail:StackInfo pos="24" ip="0xb7599902" rel="0x1dc902" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZNK12SfxViewShell18SetCurrentDocumentEv+0x30"/>
<errormail:StackInfo pos="25" ip="0xb7599f93" rel="0x1dcf93" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN12SfxViewShell8ActivateEh+0x91"/>
<errormail:StackInfo pos="26" ip="0xa9b20f33" rel="0x85df33" name="libswli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN6SwView8ActivateEh+0x1cf"/>
<errormail:StackInfo pos="27" ip="0xb75e88b5" rel="0x22b8b5" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="28" ip="0xb75d694e" rel="0x21994e" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="29" ip="0xb75b350c" rel="0x1f650c" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN12SfxViewFrame10DoActivateEhPS_+0x32"/>
<errormail:StackInfo pos="30" ip="0xb744f26d" rel="0x9226d" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="31" ip="0xb75b67af" rel="0x1f97af" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN12SfxViewFrame12SetViewFrameEPS_+0x1d"/>
<errormail:StackInfo pos="32" ip="0xb75bdc0c" rel="0x200c0c" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="33" ip="0xb75c4e3a" rel="0x207e3a" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN11SfxTopFrame14InsertDocumentEP14SfxObjectShell+0x862"/>
<errormail:StackInfo pos="34" ip="0xb745f473" rel="0xa2473" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="35" ip="0xb75a357e" rel="0x1e657e" name="libsfxli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="36" ip="0xaccc5166" rel="0x131166" name="libfwkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="37" ip="0xaccc62f1" rel="0x1322f1" name="libfwkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="38" ip="0xaccba73f" rel="0x12673f" name="libfwkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="39" ip="0xaccbaa48" rel="0x126a48" name="libfwkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="40" ip="0xb78dc80c" rel="0xac80c" name="libcomphelp4gcc3.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN10comphelper19SynchronousDispatch8dispatchERKN3com3sun4star3uno9ReferenceINS4_10XInterfaceEEERKN3rtl8OUStringESD_lRKNS4_8SequenceINS3_5beans13PropertyValueEEE+0x4d8"/>
<errormail:StackInfo pos="41" ip="0xb7df219a" rel="0x3119a" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="42" ip="0xb7e04deb" rel="0x43deb" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="43" ip="0xb7dd7acf" rel="0x16acf" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="44" ip="0xb7de0e88" rel="0x1fe88" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="45" ip="0xb7de0fa1" rel="0x1ffa1" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="46" ip="0xb7de1090" rel="0x20090" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="47" ip="0xb6ad9dc0" rel="0x264dc0" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="48" ip="0xb4c12dee" rel="0x4ddee" name="libvclplug_genli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN10SalDisplay21DispatchInternalEventEv+0xb6"/>
<errormail:StackInfo pos="49" ip="0xb51d5975" rel="0x13975" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="50" ip="0xb51d5adf" rel="0x13adf" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="51" ip="0xb4c731e1" rel="0x361e1" name="libglib-2.0.so.0" path="/usr/lib/"/>
<errormail:StackInfo pos="52" ip="0xb4c74dd6" rel="0x37dd6" name="libglib-2.0.so.0" path="/usr/lib/" ordinal="g_main_context_dispatch+0x176"/>
<errormail:StackInfo pos="53" ip="0xb4c78193" rel="0x3b193" name="libglib-2.0.so.0" path="/usr/lib/"/>
<errormail:StackInfo pos="54" ip="0xb4c7874e" rel="0x3b74e" name="libglib-2.0.so.0" path="/usr/lib/" ordinal="g_main_context_iteration+0x6e"/>
<errormail:StackInfo pos="55" ip="0xb51d5a32" rel="0x13a32" name="libvclplug_gtkli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="56" ip="0xb4c1a8fa" rel="0x558fa" name="libvclplug_genli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN14X11SalInstance5YieldEbb+0x2c"/>
<errormail:StackInfo pos="57" ip="0xb6903bdf" rel="0x8ebdf" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN11Application5YieldEb+0x5f"/>
<errormail:StackInfo pos="58" ip="0xb6903c31" rel="0x8ec31" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_ZN11Application7ExecuteEv+0x2f"/>
<errormail:StackInfo pos="59" ip="0xb7de3f8e" rel="0x22f8e" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="60" ip="0xb69095e0" rel="0x945e0" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/"/>
<errormail:StackInfo pos="61" ip="0xb690976b" rel="0x9476b" name="libvclli.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="_Z6SVMainv+0x29"/>
<errormail:StackInfo pos="62" ip="0xb7e0c1ab" rel="0x4b1ab" name="libsofficeapp.so" path="/opt/openoffice.org/basis3.0/program/" ordinal="soffice_main+0xdb"/>
<errormail:StackInfo pos="63" ip="0x8048dea" rel="0xdea" name="soffice.bin" path="/opt/openoffice.org3/program/" ordinal="main+0x16"/>
<errormail:StackInfo pos="64" ip="0xb796a450" rel="0x16450" name="libc.so.6" path="/lib/tls/i686/cmov/" ordinal="__libc_start_main+0xe0"/>
<errormail:StackInfo pos="65" ip="0x8048d41" rel="0xd41" name="soffice.bin" path="/opt/openoffice.org3/program/" ordinal="__gxx_personality_v0+0x31"/>
</errormail:Stack>
<errormail:Checksums type="MD5">
<errormail:Checksum sum="0x194687215DD7D8289267F3041665AC61" bytes="1790624" file="libuno_sal.so.3"/>
<errormail:Checksum sum="0x194687215DD7D8289267F3041665AC61" bytes="1790624" file="libuno_sal.so.3"/>
<errormail:Checksum sum="0x479485DE58DC7D8B633D333D1C1A9C33" bytes="1364388" file="libc.so.6"/>
<errormail:Checksum sum="0xDC1A871C3322BC07916DE8345FC094D7" bytes="846672" file="libstdc++.so.6"/>
<errormail:Checksum sum="0xDC1A871C3322BC07916DE8345FC094D7" bytes="846672" file="libstdc++.so.6"/>
<errormail:Checksum sum="0xDC1A871C3322BC07916DE8345FC094D7" bytes="846672" file="libstdc++.so.6"/>
<errormail:Checksum sum="0xDC1A871C3322BC07916DE8345FC094D7" bytes="846672" file="libstdc++.so.6"/>
<errormail:Checksum sum="0x64BC981845276F06D1FB273CCBBBABAE" bytes="541136" file="deploymentli.uno.so"/>
<errormail:Checksum sum="0x64BC981845276F06D1FB273CCBBBABAE" bytes="541136" file="deploymentli.uno.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xB06E0ECBD64C6AE96F5C65A8CAFD397A" bytes="1359052" file="libsbli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0x8E3F878DCC348A5A39541AD0DA38EED7" bytes="10635660" file="libswli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0xC0886264D619D1087F145A732FB3EE08" bytes="3656052" file="libsfxli.so"/>
<errormail:Checksum sum="0x3D3B026C8B1695BD37370EBCE64ABCB7" bytes="2838272" file="libfwkli.so"/>
<errormail:Checksum sum="0x3D3B026C8B1695BD37370EBCE64ABCB7" bytes="2838272" file="libfwkli.so"/>
<errormail:Checksum sum="0x3D3B026C8B1695BD37370EBCE64ABCB7" bytes="2838272" file="libfwkli.so"/>
<errormail:Checksum sum="0x3D3B026C8B1695BD37370EBCE64ABCB7" bytes="2838272" file="libfwkli.so"/>
<errormail:Checksum sum="0x2BC5CB7143A248F06F9E38E80F27A32A" bytes="1190020" file="libcomphelp4gcc3.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x5D9DF3176987A612A6BA1F7D34E94492" bytes="482540" file="libvclplug_genli.so"/>
<errormail:Checksum sum="0x56A4C9FD627704C2834403C8DEA1F074" bytes="302924" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0x56A4C9FD627704C2834403C8DEA1F074" bytes="302924" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0x985241537EF5AABDE7E731B435A71140" bytes="723948" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x985241537EF5AABDE7E731B435A71140" bytes="723948" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x985241537EF5AABDE7E731B435A71140" bytes="723948" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x985241537EF5AABDE7E731B435A71140" bytes="723948" file="libglib-2.0.so.0"/>
<errormail:Checksum sum="0x56A4C9FD627704C2834403C8DEA1F074" bytes="302924" file="libvclplug_gtkli.so"/>
<errormail:Checksum sum="0x5D9DF3176987A612A6BA1F7D34E94492" bytes="482540" file="libvclplug_genli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x811C93870E32D283207356314A0BE6A0" bytes="3500364" file="libvclli.so"/>
<errormail:Checksum sum="0x766F381C79182B34AD146477DB0C3786" bytes="408496" file="libsofficeapp.so"/>
<errormail:Checksum sum="0xAC7B2AC6E18BB0BA3B25A6D06FB051D7" bytes="7472" file="soffice.bin"/>
<errormail:Checksum sum="0x479485DE58DC7D8B633D333D1C1A9C33" bytes="1364388" file="libc.so.6"/>
<errormail:Checksum sum="0xAC7B2AC6E18BB0BA3B25A6D06FB051D7" bytes="7472" file="soffice.bin"/>
</errormail:Checksums>
</errormail:errormail>
_____

Thanks
kshsj777

---

### Post by danicruzm on 2008-11-18
Hi, I have the same problem, has found the solution?

Thanks

---

### Post by rfurman24 on 2008-11-19
Same problem here.

---

### Post by rfurman24 on 2008-11-19
I can use it as root but not otherwise.

---

### Post by rfurman24 on 2008-11-19
I am sure there is an easier way but I uninstalled Open Office and all Open Office.bins in /usr/bin including soffice. Then I reinstalled all the Open Office packages and then manually edited my menu to point to the new /usr/bin .bins.

---

### Post by MysticEdge on 2008-11-19
And this fixed your problems with Open Office crashing? Because it's been giving me some trouble as well. Which is a concern, as word processing is my primary use of my laptop.

---

### Post by rfurman24 on 2008-11-20
It would not even start. It would say it needed to recover the last document I had attempted to open and then crash. This did fix my concern.

---

### Post by TWFJR on 2008-11-21
I reported to Launchpad with no success. Launchpad's reply was that the problem must be a driver and they don't deal with drivers. I searched the internet and found Susie, Window and Ubuntu users having problems with Open Office crashing.  What gives.  It was working and I thought that the problem went away until trying my third save.  When is Ubuntu going to address this issue? Is this a driver problem?

I am using Open Office 2.4? Is this a problem with 8.10 or with all distributions including Windows? Others were using other versions of Open Office.

---

### Post by TWFJR on 2008-11-25
Getting no instruction as to what the problem is with Open Office 2.4 crashing in 8.10 I decided to take others advise that removing 2.4 and replacing it with a version from OpenOffice.org was worth a try.  I found a suggestion that if you downloaded the repository for Open Office one could do an upgrade.  Which means no need to delete everything having to do with  Ubuntu Open Office.  It worked! The upgrade did all the work.  

Go to this web page to fix Open Office crashes:

[http://community.zdnet.co.uk/blog/0,1000000567,10009699o-2000498448b,00.htm](http://community.zdnet.co.uk/blog/0,1000000567,10009699o-2000498448b,00.htm)

---

### Post by frankleeee on 2008-11-25
> **TWFJR said:**
> Getting no instruction as to what the problem is with Open Office 2.4 crashing in 8.10 I decided to take others advise that removing 2.4 and replacing it with a version from OpenOffice.org was worth a try.  I found a suggestion that if you downloaded the repository for Open Office one could do an upgrade.  Which means no need to delete everything having to do with  Ubuntu Open Office.  It worked! The upgrade did all the work.  

Go to this web page to fix Open Office crashes:

[http://community.zdnet.co.uk/blog/0,1000000567,10009699o-2000498448b,00.htm](http://community.zdnet.co.uk/blog/0,1000000567,10009699o-2000498448b,00.htm)

I used the third party portion of ubuntu tweak to install the launchpad repo and haven't had a problem on 3 different computers.That is what this link suggests is the launchpad repo.

There are repository links to Hardy,Intrepid,and Jaunty on launchpads site, actually all you have to due is change the name in the deb.

---

### Post by Hagar Delest on 2008-11-27
For the crashes, you can also try to reset your OOo user profile (see [[Tutorial] The OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=12426)), especially if you've transfered your personal data during the welcome process. The import of the old profiles can sometimes be inconsistent.

---

