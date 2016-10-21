# Poof!
Poof will spoof the location of your iOS device on Find my Friends and Find my iPhone to anywhere in the world!

**To use Poof:** *python poof.py*

Poof allows you to spoof just FMF, just FMIP, or both.

Apple does not appear to store UDID information as of iOS 9, so currently, you have to manually enter the UDID of the device that you want to spoof location data for. If you do not have or do not want to use your appleID / password, you can also use a MobileMeAuthToken.

**Poof** will spoof your location every 5 seconds until you terminate the program. You can run it in the background and forget about it, or run it 24/7 on a device that can always be powered on, like the Raspberry Pi. You can run poof for years without it locking you out of your account, due to the way that poof retrieves authentication tokens.

---

**Example**: *python poof.py* 
```
[INPUT]

Would you like to use GPS coordinates [1] or a street address [2]: 2

Apple ID: appleID

Password: password

Street address: Empire State Building 

City: NY

State: NY

Got GPS coordinates <40.7484405:-73.9856644> for Empire State Building, NY, NY

UDID: UDID of device that you want to spoof location of

Spoof FMF, FMI, or both: [0, 1, 2] 2
```
```
[OUTPUT]

Successfully changed FindMyiPhone location to <40.7484405;-73.9856644>!

Successfully changed FindMyFriends location to <40.7484405;-73.9856644>!

Waiting 5 seconds to send FMI/FMF spoof again.

^C

Terminate signal received. Stopping spoof.

Resetting location to approximate Wi-Fi AP latitude and longitude

Successfully changed FindMyFriends location to <xx.xxxx;-xx.xxxx>!

Successfully changed FindMyiPhone location to <xx.xxxx;-xx.xxxx>!

Reset location to <xx.xxxx:-xx.xxx> based on IP xxx.xxx.xxx.xxx.
```
If you enter an invalid UDID, Poof will not be able to verify if the location has been spoofed (see below). So make sure that the UDID is valid.

---

Future features: 
- [ ] Find the UDID of all devices linked to the iCloud account 
- [x] Find Friends of Friends - Basically the same as FMF, but this will find the friends of any iCloud account, with just a MMeAuthToken! *See FriendsOfFriends repo*
- [x] Confirm that the location has changed by making a request to iCloud to get the location of the device in question. This causes problems, however, if you pass in only your MMeAuthToken. *User may notice that their device's locations are being requested. A design goal of POOF is to be 100% silent, so this feature will not be implemented*
- [x] Pull old location from iCloud instead of IP address. See above note for possible issues with this. *See above note*
