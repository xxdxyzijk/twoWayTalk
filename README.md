<!--
* @Author: git config user.name
* @Date: 2025-02-10 14:25:56
 * @LastEditTime: 2025-02-10 15:18:50
 * @LastEditors: git config user.name
* @Description:
-->
# Audio Intercom Operation Instructions


## 1. Preparation
1. Open the talk.html file using a modern browser such as **Chrome**.
2. Allow the browser to access the microphone (an authorization prompt will pop up when used for the first time).
3. Prepare the following parameters:
- **Request address**: backend service address (example: `https://www.mettaxiot.com`)
- **Token**: authentication token (long string)
- **Device ID**: unique identifier of the target device.

---

## 2. Operation steps

### 1. Connect the device
1. Fill in the page input box:
- **Request address**: Enter the backend service address
- **Token**: Paste the authentication token
- **Receive the audio from device**: Enter the device ID
2. Click **`connectWs`** button to establish a WebSocket connection
- Display *"Socket is open..."* if successful
- Check if the network or parameters are correct if failed

### 2. Send audio to the device
1. **Open the microphone**:
- Click **`OpenMic`** button to authorize microphone access
2. **Start recording**:
- Click **`Start`** button to start recording
- The page will display a sound wave animation (gray box area). At this time, if you speak into the microphone, the sound wave animation will fluctuate in real time
3. **Stop recording**:
- Click the **`Stop`** button to end recording
- The recording data will be automatically sent to the device via WebSocket

### 3. Receive device audio
- The audio sent by the device will be automatically played
- The player is hidden at the bottom of the page (you can manually display the `<audio>` element to control the volume)

### 4. Disconnect
- Click the **`closetWs`** button to close the WebSocket connection
- Display *"Socket is close"* when successful

---

## III. Common problems
### 1. The microphone cannot be enabled
- Check the browser permission settings to ensure that the microphone is allowed to access
- Refresh the page and click **`OpenMic`** again

### 2. WebSocket connection failed
- Confirm whether the request address contains a protocol header 
- Check whether the token is expired or contains special characters
- Check the browser console for errors (press F12 to open the developer tool)

### 3. No sound playback
- Check whether the device successfully sends audio
- Confirm that the page is not muted (check the hidden `<audio>` element status)

---

## Ⅳ. Notes
1. **Keep the network stable**: Manual reconnection is required after WebSocket is disconnected
2. **Security Tip**: Token is sensitive information, please do not disclose