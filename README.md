# Experimental USB Flash Drive

Install apps on USB Drive, keep personal files with password(not really secure/encrypted).

# Install apps

Most installers for apps let you choose where to install. The default directory is C:/Program files/app-name. Change it to USBDRIVELETTER:/ProgframFiles/appname, and edit AppLaunch at root. To install firefox change AppLaunch.:
```@echo off
echo Welcome to Experimental Pen Drive
echo Your data - any computer
echo Choose option
echo 1 - test (test)
if %id%==1 start ProgramFiles/app/app.exe
```
to
```@echo off
echo Welcome to Experimental Pen Drive
echo Your data - any computer
echo Choose option
echo 1 - Mozilla Firefox (web browser)
if %id%==1 start ProgramFiles/firefox/firefox.exe
```

# User System

There are two methods for locking folders. Default passwords: User: password, iUser: oof.

Method 1 (LETTER:\\Users\User\Log in.bat):
```@ECHO OFF
echo Log in (as User)
echo Password:
if EXIST "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" goto UNLOCK
if NOT EXIST Private goto MDPrivate
:CONFIRM
goto LOCK
echo Invalid choice.
goto CONFIRM
:LOCK
ping 192.0.0.1 -n 1 -w 500 > nul
ren Private "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
attrib +h +s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
goto End
:UNLOCK

set/p "pass=>"
if NOT %pass%== PASSWORD-HERE goto FAIL
ping 192.0.0.1 -n 1 -w 500 > nul
attrib -h -s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
ren "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" Private
goto End
:FAIL
color 04
goto UNLOCK
:MDPrivate
md Private
echo Private created successfully
goto End
:End
```
Method 2 (LETTER:\Users\iUser\Log IN.bat):
```@echo off
echo UNLOCK(1) LOCK(2)
set /p id="Enter option:"
if %id%==2 attrib +h Locker
if %id%==1 set /p p="Enter password:"
if %p%== PASSWORD-HERE attrib -h Locker
```
Change YOUR-PASSWORD to the password you want to use. Don't forget to save thte file! Warning: This isn't as secure as encrypting.Everyone can just right click>edit and check the password, (method 1)Use the search bar, or (method 2)Enable hidden files.
