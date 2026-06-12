---
title: "Installing M$ Excel 2003 Viewer over Wine has error"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-12-18
I have tried installing Excel 2003 Viewer (I previously install PPT Viewer 2003 and made a success) and I receive "Installation ended prematurely because of an error". I didn't see any folders on Program Files meaning, installation really made an error. Here is the execution lines on the terminal:
 
```

[EMAIL="helpdesk@ubuntu:/home/softwares$"]helpdesk@ubuntu:/home/softwares$[/EMAIL] wine xlviewer.exe fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:CheckTokenMembership ((nil) 0x16a8e0 0x346d20) stub!
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 ServerAllocSize of 8 ignored for parameter 0
fixme:rpc:NdrStubCall2 ServerAllocSize of 8 ignored for parameter 1
err:rpc:I_RpcReceive we got fault packet with status 0x6be
fixme:advapi:CheckTokenMembership ((nil) 0x186118 0x341b54) stub!
fixme:advapi:LookupAccountNameW (null) L"helpdesk" (nil) 0x34f808 (nil) 0x34f804 0x34f810 - stub
fixme:advapi:LookupAccountNameW (null) L"helpdesk" 0x179218 0x34f808 0x179230 0x34f804 0x34f810 - stub
err:msi:msi_dialog_oncommand button click from nowhere 0x1c5a98 67108864 0x6002eerr:msi:msi_dialog_oncommand button click from nowhere 0x1c5a98 67108864 0x6002eerr:richedit:RTFCharSetToCodePage RTFCharSetToCodePage: unknown charset 4293967296
fixme:font:WineEngCreateFontInstance Untranslated charset 192
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 ServerAllocSize of 8 ignored for parameter 1
fixme:rpc:NdrStubCall2 ServerAllocSize of 8 ignored for parameter 1
fixme:rpc:NdrStubCall2 ServerAllocSize of 8 ignored for parameter 1
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:msi:msi_dialog_set_font No font entry for L"71"
err:msi:msi_dialog_set_font No font entry for L"100"
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:NdrClientCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 new correlation description not implemented
fixme:rpc:NdrStubCall2 ServerAllocSize of 8 ignored for parameter 1
fixme:rpc:NdrStubCall2 ServerAllocSize of 8 ignored for parameter 1
fixme:rpc:NdrStubCall2 ServerAllocSize of 8 ignored for parameter 1
err:rpc:I_RpcReceve we got fault packet wstatur 0x6br
err:ms:ITERATE_Actions Execution halted, action L"StartCache" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"

```
 
Hope you might help.

---

### Post by dbbolton on 2006-12-18
the only thing i can suggest, is slowly habituate yourself to ooo

---

