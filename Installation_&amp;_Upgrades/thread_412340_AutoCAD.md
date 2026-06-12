---
title: "AutoCAD"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by Palko on 2007-04-18
Hello,

I've installed and step up wine 9.22 on ubuntu 6.10, and I've also installed autoCAD 2002 into wine as so,

/home/pinky/.wine/drive_c/Program Files/AutoCAD

and I have all the *.dll files I need are here and I can see them when I look in the folder,

/home/pinky/.wine/drive_c/Program Files/Common Files/Autodesk Shared

Note: sorry yes I'm a noob

now I punch into my Terminal – “wine start acad.exe”and I get “err:module:import_dll Library” as so,

pinky@Pinky:~$ wine start acad.exe
libGL warning: 3D driver claims to not support visual 0x4b
fixme:exec:SHELL_execute flags ignored: 0x00000500
pinky@Pinky:~$ err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adui15.dll") not found
err:module:import_dll Library adui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\ANav.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\ANav.dll") not found
err:module:import_dll Library ANav.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adui15.dll") not found
err:module:import_dll Library adui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library acui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adui15.dll") not found
err:module:import_dll Library adui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adui15.dll") not found
err:module:import_dll Library adui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\ANav.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\ANav.dll") not found
err:module:import_dll Library ANav.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\heidi7.dll") not found
err:module:import_dll Library heidi7.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dswhip.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\heidi7.dll") not found
err:module:import_dll Library heidi7.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dlint7.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dlint7.dll") not found
err:module:import_dll Library dlint7.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dswhip.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dswhip.dll") not found
err:module:import_dll Library dswhip.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\heidi7.dll") not found
err:module:import_dll Library heidi7.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\program files\\common files\\Autodesk shared\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adctrls.dll") not found
err:module:import_dll Library adctrls.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe" failed, status c0000135

what am I doing wrong? how can I fix it?

now I have asked the wine forums but still haven't got a reply as of yet,

thank you

---

### Post by david_kt on 2007-04-18
Could you try to copy all your dll from 

/home/pinky/.wine/drive_c/Program Files/Common Files/Autodesk Shared

to:

/home/pinky/.wine/drive_c/windows/system32

DK

---

### Post by Palko on 2007-04-26
I tried and its didn't work :( 

got another ideas DK ? and thank you for your time.



pinky@Pinky:~$ wine start acad.exe
libGL warning: 3D driver claims to not support visual 0x4b
fixme:exec:SHELL_execute flags ignored: 0x00000500
pinky@Pinky:~$ err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adui15.dll") not found
err:module:import_dll Library adui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\ANav.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\ANav.dll") not found
err:module:import_dll Library ANav.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adui15.dll") not found
err:module:import_dll Library adui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acui15.dll") not found
err:module:import_dll Library acui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adui15.dll") not found
err:module:import_dll Library adui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adui15.dll") not found
err:module:import_dll Library adui15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\ANav.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\ANav.dll") not found
err:module:import_dll Library ANav.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\heidi7.dll") not found
err:module:import_dll Library heidi7.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dswhip.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\heidi7.dll") not found
err:module:import_dll Library heidi7.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dlint7.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dlint7.dll") not found
err:module:import_dll Library dlint7.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dswhip.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\dswhip.dll") not found
err:module:import_dll Library dswhip.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\heidi7.dll") not found
err:module:import_dll Library heidi7.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\ac1st15.dll") not found
err:module:import_dll Library ac1st15.dll (which is needed by L"C:\\windows\\system32\\sharedb15.dll") not found
err:module:import_dll Library sharedb15.dll (which is needed by L"C:\\windows\\system32\\acdb15.dll") not found
err:module:import_dll Library acdb15.dll (which is needed by L"C:\\windows\\system32\\acutil15.dll") not found
err:module:import_dll Library acutil15.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"C:\\windows\\system32\\acrx15.dll") not found
err:module:import_dll Library acrx15.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\adctrls.dll") not found
err:module:import_dll Library adctrls.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\pinky\\.wine\\drive_c\\Program Files\\AutoCAD\\acad.exe" failed, status c0000135
pinky@Pinky:~$

---

### Post by lathanial on 2007-07-24
Hi Palko,
Did you fix your problem? I had the same problems with AutoCAD LT 2002. The fix is to edit the registry with the correct paths. If you are still stuck I would be glad to give you the details. 

I'm hoping you've already gotten past this and are happily cadding your days away. If that is the case I would like to pick your brain if you have the time. My problem at the moment is when AutoCAD comes up if falls over when it tries to run the TODAY startup dialog. I need to figure out how to fix or disable the startup diaglog and go to the next problem - whatever that might be

Thanks
lathanial

---

### Post by misterpinkey on 2007-08-04
> **lathanial said:**
> Hi Palko,
Did you fix your problem? I had the same problems with AutoCAD LT 2002. The fix is to edit the registry with the correct paths. If you are still stuck I would be glad to give you the details. 

I'm hoping you've already gotten past this and are happily cadding your days away. If that is the case I would like to pick your brain if you have the time. My problem at the moment is when AutoCAD comes up if falls over when it tries to run the TODAY startup dialog. I need to figure out how to fix or disable the startup diaglog and go to the next problem - whatever that might be

Thanks
lathanial

Would you mind sending me the details of the registry paths you used? I'm trying to configure Autodesk Revit & Architectural Desktop.

Thanks,
MP

---

### Post by emrextreme on 2007-08-04
Here is a howto;

[http://doctus.net/showthread.php?t=17006](http://doctus.net/showthread.php?t=17006)

---

### Post by lathanial on 2007-09-05
> **misterpinkey said:**
> Would you mind sending me the details of the registry paths you used? I'm trying to configure Autodesk Revit & Architectural Desktop.

Thanks,
MP

Hello misterpinkey,
Sorry to take so long to respond but here's what I've go.
I've been trying to run AutoCAD LT 2002 in a Win98 bottle and had the problems posted by Palko. If you run regedit and go to the following key and copy the path for ACLT

HKEY_LOCAL_MACHINE\Software\Autodesk\AutoCAD LT\R8\ACLT-1:409

then go to the following key and append it to the PATH variable.

HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Environment

Hopefully you can modify to work with Autodesk Revit & Architectural Desktop. I've never used these and don't know if they are set up similar to AutoCAD LT.  Currently I'm stuck and have put it down for a while. I get into AutoCAD and it looks like all is well for about 10 seconds and then falls over with:
FATAL ERROR: Unhandled Access Violation Reading 0x0040 Exception at 6ce39eh

Once again, I apologize for taking so long to send.

Lathanial

---

### Post by david_kt on 2007-09-22
Recently I tried A9CAD, the standard product is free:

[http://www.a9tech.com/](http://www.a9tech.com/)

It could run in wine without any tweaking, just make sure you have standard wine setting (original). To do that, create separate bottle:

```
wineprefixcreate --prefix .wine_cad

env WINEPREFIX=~/.wine_cad  wine A9CADV2Setup.exe
```

It help you to create launcher as well although the icon is not registered properly. You could change the icon easily if you want.

It could be your default program as well for dwg file, just do below steps:

Right any dwg file, choose properties, and than choose open-with tab, click add, and choose A9CAD. It will autonatically open with A9CAD when you double click any dwg file.

If double clicking dwg do not show any drawing, you have to open those files from A9CAD (it happen to some of the computers I installed).

DK

---

### Post by hardyn on 2007-09-22
acad14 is the last autodesk release that will work easily with wine.
it is well documented how to make it run.

it would be more worth your time to buy a old OEM version of XP and dual boot.

---

### Post by mb125 on 2008-04-20
How about REVIT? i really dont want to switch between winblows, i also use acad 14 with wine, no problems so far.

---

### Post by hardyn on 2008-04-22
Revit is very much tied to windows, and being a full 3D BIM package, if you could get the hardware video acceleration to work correctly, i don't think you would want to take the hit in system performance.

It would be the analog of running solidworks, inventor or whatnot in wine.

---

### Post by mb125 on 2008-04-25
Recently ive played with cycas, i still have to figure what does what, but is there any BIM software for linux.

---

### Post by zipperback on 2008-05-29
[http://www.varicad.com/en/home/](http://www.varicad.com/en/home/)

Runs on both windows and linux.

It appears to be a very complete CAD system.

Hope this helps you.
- zipperback
:popcorn:

---

### Post by mb125 on 2008-05-30
Cool... i just downloaded and will be trying it out shortly

---

