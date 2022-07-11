# Serve a Scikit-Learn model using Docker and FastAPI

```bash
pip install -r requirements.txt
python code/train.py

uvicorn main:app
curl -X GET http://localhost:8000/info

# visit http://localhost:8000/docs to swagger UI

docker build . -t model_serving
docker run -p 8000:8000 model_serving

curl -H "Content-Type: application/json" -d '{
  "concavity_mean": 0.3001,
  "concave_points_mean": 0.1471,
  "perimeter_se": 8.589,
  "area_se": 153.4,
  "texture_worst": 17.33,
  "area_worst": 2019.0
}' -XPOST http://0.0.0.0:8000/predict
```

