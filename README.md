 Poaching Detection using YOLOv8 and Object Tracking
 Overview
This project implements an AI-powered poaching detection system that uses YOLOv8 for object detection and DeepSORT for object tracking. It can identify humans and animals in wildlife surveillance footage and raise alerts if poaching activity is suspected.

Poaching is a major threat to endangered species. This system aims to help forest rangers by automating the detection process in real-time, reducing response time, and improving monitoring efficiency.

 Features
Real-time detection of humans and animals in video streams.

Multi-object tracking using DeepSORT to follow entities over time.

Suspicious activity detection based on proximity and time.

Customizable rules for triggering poaching alerts.

Works with:

Live camera feeds (CCTV, drones)

Pre-recorded videos

Wildlife datasets

 Project Structure
bash
Copy
Edit
poaching-detection/
│── data/                  # Datasets & sample videos
│── models/                # YOLOv8 weights
│── outputs/               # Processed videos & logs
│── detect.py               # Main detection & tracking script
│── requirements.txt        # Python dependencies
│── README.md               # Project documentation
 Workflow
Object Detection

YOLOv8 detects humans, animals, and other relevant objects.

The model outputs bounding boxes, labels, and confidence scores.

Object Tracking

DeepSORT assigns a unique ID to each detected object and tracks it across frames.

Poaching Rule Engine

Flags potential poaching scenarios, e.g.:

Human within a certain distance of an animal for a prolonged period.

Humans in restricted zones at unusual times.

Alert System

Alerts are logged in real-time.

Can be extended to send SMS, email, or mobile notifications.

 Installation
 Clone the repository
bash
Copy
Edit
git clone https://github.com/yourusername/poaching-detection.git
cd poaching-detection
 Create a virtual environment
bash
Copy
Edit
python -m venv venv
source venv/bin/activate   # On Linux/Mac
venv\Scripts\activate      # On Windows
 Install dependencies
bash
Copy
Edit
pip install -r requirements.txt
 Download YOLOv8 weights
You can use YOLOv8 pre-trained weights or train your own. Example:

bash
Copy
Edit
yolo download model=yolov8n.pt
Or place your custom weights in the models/ folder.

 Usage
Detect in a video
bash
Copy
Edit
python detect.py --source data/sample_video.mp4 --weights models/yolov8n.pt
Detect from a live camera feed
bash
Copy
Edit
python detect.py --source 0 --weights models/yolov8n.pt
(Replace 0 with the camera index or RTSP URL.)
![Output Screenshot](Screenshot%202025-08-11%20111947.png)

Detect with custom rules
bash
Copy
Edit
python detect.py --source data/sample_video.mp4 --weights models/yolov8n.pt --alert_distance 20 --alert_time 10
Author
Sagnik Patra
