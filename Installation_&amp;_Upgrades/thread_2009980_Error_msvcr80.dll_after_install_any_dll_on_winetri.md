---
title: "Error msvcr80.dll after install any dll on winetricks!"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by Th3Walker on 2012-06-25
[B][COLOR="Red"]------------------- ENGLISH -------------------------------------------------------
[/COLOR][/B]
When i start photoshop cs4, say me an error:

The error say: MSVCR80.dll aborting fail and other! 

I try to download the new dll to dll-fixer...

And the error always say: MSVCR80.dll aborting fail and other! 

HERE THE ERROR:

fixme: actctx : parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programmi\\PhotoshopCS4Portable\\App\\Photoshop\\Photoshop.exe" failed, status c0000142

HELP ME, I LOVE PHOTOSHOP CS4!

[B][COLOR="RoyalBlue"]----------------- ITALIAN ---------------------------------------------------------
[/COLOR][/B]
Quando avvio photoshop cs4, il terminale mi mostra un errore:

L'errore riguarda MSVCR80.dll...

Ho provato a riscaricare la dll da dll-fixer...

Ma l'errore c'è sempre...

fixme: actctx : parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programmi\\PhotoshopCS4Portable\\App\\Photoshop\\Photoshop.exe" failed, status c0000142

Aiuto, non posso stare senza photoshop cs4... Vi ringrazio!

---

### Post by dino99 on 2012-06-25
It might be helpfull to know which wine release you are using on which ubuntu distro & if its on 32 or 64 bits installation

check that you are using the latest wine, which is 1.5.7 now. You should not get this error on a clean new .wine.

---

